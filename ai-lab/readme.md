# How to create a custom workbench in OpenShift AI to deploy your own models
---

## Laboratory Description
In this laboratory we have developed an AI model that is based on image processing capable of detecting a vehicle accident based on the information that can be obtained from a photo of an accident.

Thanks to OpenShift AI, we will be able to deploy in minutes a customized execution environment (workbench) that has all the necessary tools to execute the model, such as specific Python libraries and the Jupyter solution, and we will analyze an image to see how this developed model can evaluate a claim.

![image](https://github.com/user-attachments/assets/bf8b6611-bddf-47eb-8e9c-2c5dccb4fb79)

What do we take away from this laboratory?
The idea is to learn how it is possible to use OpenShift AI to implement an Artificial Intelligence use case. To do this, it will be necessary to configure a custom model execution environment and we will see how the procedure is to execute an image recognition model.

## 1) Access OpenShift AI
---

For this lab, an OpenShift cluster has been provisioned, with OpenShift AI deployed.

Each person who completes this lab will have their own user with which they can work.

### Environmental data
In a new window, access the OpenShift AI console provided to you from the RH team.

<img width="549" alt="Screenshot 2025-03-12 at 12 31 27 PM" src="https://github.com/user-attachments/assets/42fb6d73-9c5d-404c-bbfc-8a84794bb8a9" />

Click on Login with OpenShift and log in with the following credentials:
User:
```
Will be provided by the team.
```
Password:
```
Will be provided by the team.
```

![image](https://github.com/user-attachments/assets/47679858-fddc-4a77-a231-44e4cb577192)

You can switch now to OpenShift AI Console:

You can ignore the message and continue with the lab. Once authenticated, the following console will be displayed:

<img width="1478" alt="Screenshot 2025-03-12 at 12 34 20 PM" src="https://github.com/user-attachments/assets/db7e6b7a-e8a3-44fd-90e0-53cd50b5259c" />

Congratulations! You are now connected to OpenShift AI and ready to start the lab.

## 2) Create a custom workbench
---

In OpenShift AI, a workbench is a containerized work environment that runs as a pod. Workbenches include a collection of libraries commonly used in AI/ML environments, as well as a JupyterLab server.

### Import custom image
To import a custom image, in the left navigation panel, go to Settings - Notebook images and then Import new image

![image](https://github.com/user-attachments/assets/eb084e33-1ea7-4e00-a8bf-3deb6e727b9b)

Complete the form with the following information:

Image location: 
```
quay.io/acidonpe/ocp-ai-insurance-model:1.0
```
Name: (Add Your user to the name)
```
Custom AI image User X
```
<img width="665" alt="Screenshot 2025-03-12 at 12 54 28 PM" src="https://github.com/user-attachments/assets/1d1b0d91-210b-453b-8040-18ab44afef97" />

The rest of the fields can be left blank. Then, click Import.

The image will be imported as shown below:

<img width="1241" alt="Screenshot 2025-03-12 at 12 55 08 PM" src="https://github.com/user-attachments/assets/2238589a-b25a-4d9b-a201-a40949904c2f" />

### Create workbench

Next, a workspace will be created within the user project.
Note: Your Data Science project is same as your user so for user1 it will be user1 for user2 it will be user2, etc..

Go to the left navigation panel, click Data Science Projects, and select your project.

![image](https://github.com/user-attachments/assets/0c0a1c38-c87d-46dd-af3d-87a2abf6bd94)

Within the project, select Create a workbench.

<img width="888" alt="Screenshot 2025-03-12 at 12 48 57 PM" src="https://github.com/user-attachments/assets/03ef4605-89b2-4e78-b389-9f621ba03593" />

Complete the fields with the following information:

Name: 
```
Lab Workbench
```
Image selection: //select the image you just imported in the previous step
```
Custom AI image User X
```
Deployment size: 
```
Standard
```

The remaining fields can be left with their default values. Check that the result is as follows, and click Create workbenchto create the workbench:

<img width="755" alt="Screenshot 2025-03-12 at 12 57 47 PM" src="https://github.com/user-attachments/assets/97358254-7123-4e47-b0ec-8f70668eba8f" />

### Start the workbench

Once the workbench has been created, wait for its status to change to Running, this can take minutes to pull the image and create the workbench. You can follow the progress if you click on status --> Event Log:

<img width="456" alt="Screenshot 2025-03-12 at 1 06 13 PM" src="https://github.com/user-attachments/assets/8048e932-83ef-47c0-ab7f-171d955ba5c4" />

Once it's running, we can access the work environment, to do this click on Open.

![image](https://github.com/user-attachments/assets/ef6780db-bdc2-471d-8383-4403900cb27a)

To access the workbench, you must authenticate with your OpenShift AI credentials. To do so, click lab-users and log in with the following credentials:

User:
```
Same provided User
```
Password:
```
Same provided password
```

The following permissions must then be accepted.

![image](https://github.com/user-attachments/assets/e83e8965-cd4c-4ab7-9a11-f77c21c347f9)

Once accepted, the JupyterLab server will be displayed.

![image](https://github.com/user-attachments/assets/d75516c0-b2cb-49f1-9c88-6e7820f4ed79)

Congratulations! You're now ready to deploy your AI/ML model.

## 3) Deploy the model
---

### Import model
To import the model, the first step is to clone the Git repository. To do this, click the Git icon in the left navigation menu.

![image](https://github.com/user-attachments/assets/cf209d85-70a3-40af-bbfe-17afb99267f4)

```
https://github.com/rhcs-workshops/summit-connect-madrid-openshift-ai-lab.git
```

![image](https://github.com/user-attachments/assets/218bfe99-1525-4449-adb6-6d52ddd17a7f)

Once the repository is imported into the JupyterLab server, we will access the repository by double-clicking on the . folder summit-connect-madrid-openshift-ai-lab.

![image](https://github.com/user-attachments/assets/45b68167-8a4f-4c89-a7f3-5de5f148de99)

To view the model you are going to work with, select the folder lab and open the file named accident-recog.ipynbthat contains the model.

![image](https://github.com/user-attachments/assets/7fbd030e-655c-4458-8bb1-30dd24f34b6c)

### Run model

To run the full model, click on Restart kernel and Run all Cells, and get the result.

![image](https://github.com/user-attachments/assets/ec454c10-bd85-4932-a196-c01a15f78ad1)

Click on Restart, and wait until the model finishes executing.

![image](https://github.com/user-attachments/assets/419807f8-8e94-4744-b58e-74b28d0fc17e)

Once the model has finished its execution, the result can be observed. The model has assessed the damage caused by the accident, showing the percentage of accuracy of the model.

![image](https://github.com/user-attachments/assets/ea76c56a-6439-477b-a757-a483f7a55278)

Congratulations! You've now run the AI/ML model for crash recognition using a custom image.


## References:

This is a translation and modified copy of this lab: https://rhcs-workshops.github.io/summit-connect-madrid-openshift-ai-lab/summit-ocpai-lab/index.html

