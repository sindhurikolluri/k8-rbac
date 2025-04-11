# RBAC

REGION_CODE=us-east-1
CLUSTER_NAME=expense
ACC_ID=315069654700

### Permissions

* OIDC provider
```
eksctl utils associate-iam-oidc-provider \
    --region $REGION_CODE \
    --cluster $CLUSTER_NAME \
    --approve
```

* Provide access to EKS through IAM Policy
```
eksctl create iamserviceaccount \
--cluster=$CLUSTER_NAME \
--namespace=expense \
--name=expense-secret \
--attach-policy-arn=arn:aws:iam::717279725557:policy/ExpenseMySQLSecretManager \
--override-existing-serviceaccounts \
--region $REGION_CODE \
--approve
```