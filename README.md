# Enable Resolver Query logs for member accounts

As part of the CISO tools onboarding (Splunk), VPC Flow logs will be enabled in all the member account VPC. This is achived through a Config rule that constantly checks the Flow logs enabled status on every VPCs. The diagram below explains the architecture,

![Figure: VPC Flow logs](enable-vpc-flow-architecture.png)

## Prerequisites

The following prerequisites must be in place in order to run this cloudformation template,

* An S3 bucket exists in the Log Archive account (Central Account) with trust relationship for member accounts to write the logs.

## Solution Resources

The CloudFormation template will create following resources in the member account,

* AWS SSM Document :  `Kyndryl-CTO-AWS-EnableVPCFlowLogs`
* AWS Config Rule  : `KyndrylCTOConfigRuleForVPCFlowLogsTagging`
* AWS Config Remediation Configuration : `KyndrylCTOConfigRuleForVPCFlowLogsTagging`
* AWS IAM Role : `KyndrylVPCFlowlogs-ConfigRemediationRole-xxxxxxxx`

## Solution Deployment

1. Navigate to the AWS Management Account console
2. Create a CloudFormation Stackset
3. Use the CloudFormation Stackset provided as part of this documentation. CloudFormation Source File : [aws-config-remediate-vpc-flow-logs-custom.yaml](aws-config-remediate-vpc-flow-logs-custom.yaml)
4. Select Accounts and Regions
5. Deploy the Stackset
