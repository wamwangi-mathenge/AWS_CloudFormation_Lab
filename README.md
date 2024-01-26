# Lab - Automation with CloudFormation

Deploying infrastructure in a consistent, reliable manner is difficult — it requires people to follow documented procedures without taking any undocumented shortcuts. Plus, it can be difficult to deploy infrastructure out-of-hours when less staff are available. AWS CloudFormation changes this by defining infrastructure in a template that can be automatically deployed — even on an automated schedule. This lab provides experience in deploying and editing CloudFormation stacks. It is an interactive experience, requiring you to consult documentation to discover how to define resources within a CloudFormation template.

## Duration

This lab will require approximately 45 minutes to complete.

## Task 1: Deploy a CloudFormation Stack

You will begin by deploying a CloudFormation stack that creates a VPC

1. Click this [link](./task1.yaml) and download the CloudFormation template: `task1.yaml`
2. Open this file in a code Editor.

Look through the file. You will notice several sections:

- The **Parameters** section is used to prompt for inputs that can be used elsewhere in the template. The template is asking for two IP address (CIDR) ranges for defining the VPC.
- The **Resources** section is used to define the infrastructure to be deployed. The template is defining the VPC, and a Security Group.
- The **Outputs** section is used to provide selective information about resources in the stack. The template is providing the Default Security Group for the VPC that is created.

The template is written in a format called YAML, which is commonly used for configuration files. The format of the file is important, including the indents and hyphens. CloudFormation templates can also be written in JSON.

You will now use this template to launch a CloudFormation stack. Wait until the status changes to `CREATE_COMPLETE`. You can click Refresh occasionally to update the display.

Optional: Go to the VPC console to see the Lab VPC that was created. Then, return to the CloudFormation console.

## Task 2: Add an Amazon S3 Bucket to the Stack

In this task, you will gain experience in editing a CloudFormation template.

Your objective is:

- Add an Amazon S3 bucket to the template
- Then update the stack with the revised template

This will result in a new bucket being deployed.

Here are some tips:

1. You should edit the `task1.yaml` file you downloaded earlier to include an Amazon S3 bucket
2. Use this documentation page for assistance: [Amazon S3 Template Snippets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/quickref-s3.html)
3. You do not require any Properties for this bucket resource

Once you have edited the template, continue to update the stack.

After a minute, the stack status will change from `UPDATE_IN_PROGRESS` to `UPDATE_COMPLETE`.

The bucket will now be displayed in the list of resources. CloudFormation will have assigned it a random name so that it does not conflict with any existing buckets.

## Task 3: Add an Amazon EC2 Instance to the Stack

In this task, your objective is to add an Amazon EC2 instance to the template, then update the stack with the revised template.

Whereas the bucket definition was rather simple (just two lines), defining an Amazon EC2 instance is more complex because it needs to use associated resources, such as an AMI, security group and subnet.

1. Use this documentation page for assistance: [AWS::EC2::Instance](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-instance.html)

Optional: Go to the EC2 console to see the App Server that was created. Then, return to the CloudFormation console.

## Task 4: Delete the Stack

When a CloudFormation stack is deleted, CloudFormation will automatically delete the resources that it created.

You will now delete the stack.

Optional: Verify that the Amazon S3 bucket, Amazon EC2 instance and the VPC have been deleted.
