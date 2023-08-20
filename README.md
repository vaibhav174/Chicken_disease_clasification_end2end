# Chicken_disease_clasification_end2end
Build an end to end project to classify if the chicken has "Coccidiosis", "New Castle Disease" ,"Salmonella" or is.
Tools Used --> deep learning libraries, MLOps DVC, Docker, CI/CD, AWS Deployment
Complete dataset Data set --> https://www.kaggle.com/datasets/allandclive/chicken-disease-1

<b>Note:  For the pupose of demonstration this version of the project only classify between Coccidiosis and Healthy and trained on a really smaller version of the original dataset. To re-train the actual model please refer the description below and change the code accordingly</b>

## Changes for whole dataset
### ./config/config.yaml
Contains the necessary configs for each part of the pipeline.  
<b>Please Change the source data URL in the data ingestion stage to the location of complete dataset zip file on local machine. The current URL is for a smaller version of the dataset hosted on github.</b>

### ./templates/index.html
modify the html file accordingly to have space for 4 outputs

### ./params.yaml
Change the number of classes to 4 and other parameters according to your need.

## Workflows

1. Update config.yaml
2. Update secrets.yaml [Optional]
3. Update params.yaml
4. Update the entity
5. Update the configuration manager in src config
6. Update the components
7. Update the pipeline 
8. Update the main.py
9. Update the dvc.yaml


# How to run?
### STEPS:

First Clone the repository and do the changes you need to the code according to the dataset


### STEP 01- Create a conda environment after opening the repository

```bash
conda create -n cnncls python=3.8 -y
```

```bash
conda activate cnncls
```


### STEP 02- install the requirements
```bash
pip install -r requirements.txt
```

### STEP 03- Run the training pipeline 
```bash
# cmd run
python main.py
```
```bash
# dvc run
dvc repro
```

### STEP 04- Prediction using flask web application
```bash
# Finally run the following command
python app.py
```

Now,
```bash
open up you local host and port  localhost:8080
```


### DVC cmd

1. dvc init
2. dvc repro
3. dvc dag



# AWS-CICD-Deployment-with-Github-Actions

## 1. Login to AWS console.

## 2. Create IAM user for deployment

	#with specific access

	1. EC2 access : It is virtual machine

	2. ECR: Elastic Container registry to save your docker image in aws


	#Description: About the deployment

	1. Build docker image of the source code

	2. Push your docker image to ECR

	3. Launch Your EC2 

	4. Pull Your image from ECR in EC2

	5. Lauch your docker image in EC2

	#Policy:

	1. AmazonEC2ContainerRegistryFullAccess

	2. AmazonEC2FullAccess

	
## 3. Create ECR repo to store/save docker image
    - Save the URI of ECR REPO

	
## 4. Create EC2 machine (Ubuntu) 

## 5. Open EC2 and Install docker in EC2 Machine:
	
	
	#optinal

	sudo apt-get update -y

	sudo apt-get upgrade
	
	#required

	curl -fsSL https://get.docker.com -o get-docker.sh

	sudo sh get-docker.sh

	sudo usermod -aG docker ubuntu

	newgrp docker
	
# 6. Configure EC2 as self-hosted runner:
    setting>actions>runner>new self hosted runner> choose os> then run command one by one


# 7. Setup github secrets:

    AWS_ACCESS_KEY_ID=

    AWS_SECRET_ACCESS_KEY=

    AWS_REGION = us-east-1

    AWS_ECR_LOGIN_URI = demo>>  566373416292.dkr.ecr.ap-south-1.amazonaws.com

    ECR_REPOSITORY_NAME = simple-app


