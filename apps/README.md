
Test Java jar files for use with Azure Spring Cloud.

Blue App displays "Welcome to the BLUE app"

White App display "Welcome to the White app"

---

To deploy the blue-app in Azure:

az spring-cloud app create -n blue-app -s <spring-cloud-service> -g <spring-cloud-service-rg> --assign-endpoint true

az spring-cloud app identity assign -n blue-app -s <spring-cloud-service> -g <spring-cloud-service-rg>
  "identity": {
    "principalId": "aaa-bbb-ccc-ddd",

az role assignment create --assignee <principalId> --role "Storage Blob Data Contributor" --scope /subscriptions/xxx-yyy-zzz/resourceGroups/<storage-rg>/providers/Microsoft.Storage/storageAccounts/<storage-account>

az spring-cloud app deploy --verbose -n blue-app -s <spring-cloud-service> -g <spring-cloud-service-rg> --artifact-path <path>/blue-app.jar

curl https://<spring-cloud-service>-blue-app.private.azuremicroservices.io
