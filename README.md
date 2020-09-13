[![CircleCI](https://circleci.com/gh/vikrantarora14/Module4ProjectML.svg?style=svg)](https://circleci.com/gh/circleci/vikrantarora14/Module4ProjectML)

## Project Overview

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on.  This project is  to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. 

### Project files

Files in the project and their use:
1) app.py - the main python file which has logic for making predictions
2) make_predictions.sh - calls app.py to trigger predictions
3) .circleci - is a hidden folder which inturn contains config.yml for running circleci build
4) requirements.txt - necessary components to be installed for the project to run successffully
5) Makefile - you can trigger the basic setup via Makefile such as linting as well as installing all components
6) run_docker-sh - creates docker image locally
7) upload_docker.sh - uploads the docker image to dockerhub
8) run_kubernetes.sh - launches the docker image in a kubernetes cluster
9) output_txt_files contains two files:
    docker_out.txt - this contains the execution logging information when app.py is triggered via make_predictiions.sh
    kubernetes_out.txt - this contains the logs of the steps executed when ./run_kubernetes.sh is executed.

Python commands for the project
## Setup the Environment

* Create a virtualenv and activate it
python3 -m venv ~/Desktop/CloudDevOps/Microservices/Project/.devopsprojectmlmicroservicekubernetes
source python3 -m venv ~/Desktop/CloudDevOps/Microservices/Project/.devopsprojectmlmicroservicekubernetes/bin/activate

* Run `make install` to install the necessary dependencies
make install

* Run `make lint` to lint app.py and Dockerrfile
make lint

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Generating output for docker_out.txt
Execute "./run_docker.sh"
this will create docker image locally and the application will be up and running on port 8000
In parallel , execute "./make_prediction.sh"
this will make a call to app.py and the logs that are generated for the steps executed in app.py go into docker_out.txt

### Uploading docker image that has been created locally to Dockerhub repo called vikrantarora14/projectml
./upload_docker.sh

### using Dockerhub and launching the app in Kubernetes cluster
./run_kubernetes.sh
This will use the image that was uplaoded onto Dockerhub and launch it in a pod called projectml in kubernetes cluster
The applicatiion will run on port 8000

### Generating output for kubernetes_out.txt
Once the application is up and running on port 8000 once ./run_kubernetes.sh is successful, trigger ./make_prediction.sh to make a call to the application to return predictions
The logs are then copied to kubernetes_out.txt


