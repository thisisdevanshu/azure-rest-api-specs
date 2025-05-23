# DataLakeStore

> see https://aka.ms/autorest

This is the AutoRest configuration file for DataLakeStore.



---
## Getting Started
To build the SDK for DataLakeStore, simply [Install AutoRest](https://aka.ms/autorest/install) and in this folder, run:

> `autorest`

To see additional help and options, run:

> `autorest --help`
---

## Configuration



### Basic Information
These are the global settings for the DataLakeStore API.

``` yaml
openapi-type: arm
tag: package-2016-11
```


### Tag: package-2016-11

These settings apply only when `--tag=package-2016-11` is specified on the command line.

``` yaml $(tag) == 'package-2016-11'
input-file:
- Microsoft.DataLakeStore/stable/2016-11-01/account.json
```

### Tag: package-2015-10-preview

These settings apply only when `--tag=package-2015-10-preview` is specified on the command line.

``` yaml $(tag) == 'package-2015-10-preview'
title: DataLakeStoreAccountManagementClient
description: DataLake Store Client
input-file:
- Microsoft.DataLakeStore/preview/2015-10-01-preview/account.json
```

## Suppression
``` yaml
directive:
  - suppress: TrackedResourceGetOperation
    reason: This is by design in that we return DataLakeStoreAccountBasic only for Account_List
    #where:
    #  - $.definitions.DataLakeStoreAccountBasic

  - suppress: TrackedResourcePatchOperation
    reason: DataLakeStoreAccountBasic is not independent and its purpose is for Account_List only.  PATCH is for DataLakeStoreAccount, which will effectively update DataLakeStoreAccountBasic
    #where:
    #  - $.definitions.DataLakeStoreAccountBasic
```

---
# Code Generation


## Swagger to SDK

This section describes what SDK should be generated by the automatic system.
This is not used by Autorest itself.

``` yaml $(swagger-to-sdk)
swagger-to-sdk:
  - repo: azure-sdk-for-net
  - repo: azure-sdk-for-python
  - repo: azure-sdk-for-java
  - repo: azure-sdk-for-go
  - repo: azure-sdk-for-node
  - repo: azure-sdk-for-ruby
    after_scripts:
      - bundle install && rake arm:regen_all_profiles['azure_mgmt_datalake_store']
  - repo: azure-resource-manager-schemas
  - repo: azure-powershell
```


## Python

See configuration in [readme.python.md](./readme.python.md)
## Go

See configuration in [readme.go.md](./readme.go.md)

## Java

These settings apply only when `--java` is specified on the command line.
Please also specify `--azure-libraries-for-java-folder=<path to the root directory of your azure-libraries-for-java clone>`.

``` yaml $(java)
azure-arm: true
fluent: true
namespace: com.microsoft.azure.management.datalake.store
license-header: MICROSOFT_MIT_NO_CODEGEN
output-folder: $(azure-libraries-for-java-folder)/azure-mgmt-datalake/store
```

### Java multi-api

``` yaml $(java) && $(multiapi)
batch:
  - tag: package-2015-10-preview
  - tag: package-2016-11
```

### Tag: package-2015-10-preview and java

These settings apply only when `--tag=package-2015-10-preview --java` is specified on the command line.
Please also specify `--azure-libraries-for-java=<path to the root directory of your azure-sdk-for-java clone>`.

``` yaml $(tag) == 'package-2015-10-preview' && $(java) && $(multiapi)
java:
  namespace: com.microsoft.azure.management.datalakestore.v2015_10_01_preview
  output-folder: $(azure-libraries-for-java-folder)/sdk/datalakestore/mgmt-v2015_10_01_preview
regenerate-manager: true
generate-interface: true
```

### Tag: package-2016-11 and java

These settings apply only when `--tag=package-2016-11 --java` is specified on the command line.
Please also specify `--azure-libraries-for-java=<path to the root directory of your azure-sdk-for-java clone>`.

``` yaml $(tag) == 'package-2016-11' && $(java) && $(multiapi)
java:
  namespace: com.microsoft.azure.management.datalakestore.v2016_11_01
  output-folder: $(azure-libraries-for-java-folder)/sdk/datalakestore/mgmt-v2016_11_01
regenerate-manager: true
generate-interface: true
```





