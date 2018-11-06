# Application Deployment on Cloud Services
This repository contain Basic "Hello World" deployment Node application on Several Cloud Services.

## Pre-requisite
* Node Installed
```bash
node -v
```

* Clone this repository
```bash
git clone https://github.com/rijdz/cheatsheet-cloud-deployment.git
```


## Localhost
```bash
npm run start
```

## AWS


## Azure
[Source](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-get-started-nodejs) [Demo](https://rijdz-app-azure.azurewebsites.net/) 

* Install Azure CLI
[Azure-CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-macos?view=azure-cli-latest)

* Create Services by Azure CLI
```bash
# Create Resource Group
az group create --name rijdz-rg-azure --location "Southeast Asia"

# Create Service Plan
az appservice plan create --name rijdz-plan-azure --resource-group rijdz-rg-azure --sku FREE

# Create Web App Service
az webapp create --resource-group rijdz-rg-azure --plan rijdz-plan-azure --name rijdz-app-azure --deployment-local-git

# Set Nodejs Runtime
az webapp config appsettings set --resource-group rijdz-rg-azure --name rijdz-app-azure --settings WEBSITE_NODE_DEFAULT_VERSION=8.11.1

# Get remote git from azure - (Copy the result)
git config --get remote.azure.url

# Add remote git (paste) into local repository after succesfuly created
git remote add azure https://rijdz@rijdz-app-azure.scm.azurewebsites.net/rijdz-app-azure.git

# Push local repository into Remote Azure
git push origin azure

```

## Heroku
[Source](https://devcenter.heroku.com/articles/getting-started-with-nodejs)
[Demo](https://sleepy-harbor-42228.herokuapp.com/)

```bash
# Login from Heroku-CLI
heroku login

# Initialize Heroku App Instance
# skip this if instance already created on heroku
heroku create

# Make sure Heroku Instance already added as remote git
git remote -v

# If there are no heroku as remote repository, you can add with
# you can find Heroku Git Address on Heroku dashboard > settings
git remote add heroku https://git.heroku.com/sleepy-harbor-42228.git

```


* Make sure node application have default starting script on package.json
```json
"scripts": {
    "start": "node index.js"
  }
```

* Push into Heroku
```bash
git push heroku master
```
