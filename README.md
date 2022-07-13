### Description

That's a customized version of https://github.com/awslabs/aws-codedeploy-plugin.

It aims to support the current deployment process for STAGE/PROD environments that **needs** a _repositoryName_**.zip**

In order to avoid the wrong `.zip` file being generated on S3 Bucket using the actual plugin, this fork adds a property to *force* setting the zip filename.

### How to upload this plugin to Jenkins

- Build using `mvn clean install`
- Go to `Manage Plugins` > `Advanced` tab
- Upload `.hpi` file (from `target` folder)
- Restart Jenkins and see the updated Version on `Installed plugins` tab

### How to use

In your `Jenkinsfile` Codedeploy snippet:

use
`step([$class                : "AWSCodeDeployCustomPublisher",`

add
`overrideZipFileName   : "yourRepoName.zip",` (or "yourRepoName" only)

It will upload a `yourRepoName.zip` to S3.