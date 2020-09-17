# Ansible playbook RBL Autocheck via GitLab-CI

透過 GitLab-CI 進行自動化查詢外部黑名單組織，可利用`GitLab UI`與`API`的方式進行查詢，查詢之IP若被列入外部黑名單，該IP將會列入Local RBL清單，可以使用相關資安設備支援定時fetch file功能。

目前支援以下外部黑名單組織
* AbuseIPDB
* Badips
* FortiGuard

## Requirements

需定義變數名稱`RBLIP`，並給定單一IP值


### Use GitLab

Go to CI / CD -> Run Pipeline

variable key: `RBLIP`

variable value: `要查詢之IP`


### Use curl

```bash
curl -XPOST -k --form token=<GitLab Token> --form ref=master --form RBLIP=<要查詢之IP> https://<GitLab url>/api/v4/projects/<project id>/trigger/pipeline
```

## Author Information

Sam Chen