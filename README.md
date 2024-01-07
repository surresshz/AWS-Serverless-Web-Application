# **AWS Server-less Web Application**

The application architecture uses AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon Cognito, and AWS Amplify Console. Amplify Console provides continuous deployment and hosting of the static web resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser. JavaScript executed in the browser sends and receives data from a public backend API built using Lambda and API Gateway. Amazon Cognito provides user management and authentication functions to secure the backend API. Finally, DynamoDB provides a persistence layer where data can be stored by the API's Lambda function.

![Serverless_Architecture d930970c77b382db6e0395198aacccd8a27fefb7](https://github.com/surresshz/AWS-Serverless-Web-Application/assets/112921897/8768a19e-6eec-4a19-bdfc-05657c3bd2c3)

Prerequisites:- AWS CLI, ArcGIS to add mapping to your app, a text editor, and a web browser.

### **Static Web Hosting**

AWS Amplify hosts static web resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser

### **User Management**

Amazon Cognito provides user management and authentication functions to secure the backend API.

### **Server-less Backend**

Amazon DynamoDB provides a persistence layer where data can be stored by the API's Lambda function.

### **RESTful API**

JavaScript executed in the browser sends and receives data from a public backend API built using Lambda and API Gateway.

## **Module 1**

![mod1](https://github.com/surresshz/AWS-Serverless-Web-Application/assets/112921897/2e8dc890-c5d3-4305-9d05-2bb5f89108a1)

The architecture for this module is straightforward. All of your static web content including HTML, CSS, JavaScript, images, and other files will be managed by AWS Amplify Console. Your end users will then access your site using the public website URL exposed by AWS Amplify Console. You don't need to run any web servers or use other services to make your site available.

## **Module 2**

![mod2](https://github.com/surresshz/AWS-Serverless-Web-Application/assets/112921897/e789d894-da6a-4cf8-b9bb-f7419a811c13)

When users visit your website they will first register a new user account. For the purposes of this workshop we'll only require them to provide an email address and password to register. However, you can configure Amazon Cognito to require additional attributes in your own applications.
After users submit their registration, Amazon Cognito will send a confirmation email with a verification code to the address they provided. To confirm their account, users will return to your site and enter their email address and the verification code they received. You can also confirm user accounts using the Amazon Cognito console with a fake email addresses for testing.
After users have a confirmed account (either using the email verification process or a manual confirmation through the console), they will be able to sign in. When users sign in, they enter their username (or email) and password. A JavaScript function then communicates with Amazon Cognito, authenticates using the Secure Remote Password protocol (SRP), and receives back a set of JSON Web Tokens (JWT). The JWTs contain claims about the identity of the user and will be used in the next module to authenticate against the RESTful API you build with Amazon API Gateway.

## **Module 3**

![mod3](https://github.com/surresshz/AWS-Serverless-Web-Application/assets/112921897/4793be3f-744f-4716-ad09-de393b1b7348)

You will implement a Lambda function that will be invoked each time a user requests a unicorn. The function will select a unicorn from the fleet, record the request in a DynamoDB table, and then respond to the frontend application with details about the unicorn being dispatched.

The function is invoked from the browser using Amazon API Gateway. You'll implement that connection in the next module. For this module, you will just test your function in isolation.

## **Module 4**

![mod4](https://github.com/surresshz/AWS-Serverless-Web-Application/assets/112921897/980bcfbf-9f6b-419e-a283-9f09b4aed5b6)

The static website you deployed in the first module already has a page configured to interact with the API you will build in this module. The page at /ride.html has a simple map-based interface for requesting a unicorn ride. After authenticating using the /signin.html page, your users will be able to select their pickup location by clicking a point on the map and then requesting a ride by choosing the "Request Unicorn" button in the upper right corner.

This module will focus on the steps required to build the cloud components of the API, but if you're interested in how the browser code works that calls this API, you can inspect the **ride.js** file of the website. In this case, the application uses jQuery's ajax method to make the remote request.

### AWS Services used in project

- **codecommit** :-  Remote repo same as github.
- **Amplify** :- The AWS Amplify Console to deploy the website you've just committed to git.
- **Cognito** :- Amazon Cognito user pools let you add registration and sign-in to your apps. With Amazon Cognito identity pools, you can provide AWS credentials for access to your cloud resources.
- **DynamoDB** :- A fast and flexible NoSQL database service for any scale
DynamoDB is a fully managed, key-value, and document database that delivers single-digit-millisecond performance at any scale.
- **Lambda** :- lets you run code without thinking about servers. With Lambda, you can run code for virtually any type of application or backend service, all with zero administration.
- **API Gateway** :-  create, maintain, and secure APIs at any scale Amazon API Gateway helps developers to create and manage APIs to back-end systems running on Amazon EC2, AWS Lambda, or any publicly addressable web service. With Amazon API Gateway, you can generate custom client SDKs for your APIs, to connect your back-end systems to mobile, web, and server applications or services.
- **IAM** :- Created roles in this project, a web service that helps you securely control access to AWS resources. With IAM, you can centrally manage permissions that control which AWS resources users can access. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

