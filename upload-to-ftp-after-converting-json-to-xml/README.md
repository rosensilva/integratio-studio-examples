# Upload to FTP after converting JSON to XML

This example application illustrates the concept of datamapping to convert JSON data to XML. It also shows you how to 
configure and use the FTP connector to upload a file to a FTP server.

### Assumptions ###

This document assumes that you are familiar with WSO2 EI and the 
[Integration Studio interface](https://ei.docs.wso2.com/en/latest/micro-integrator/overview/quick-start-guide/). To 
increase your familiarity with Integration Studio, consider completing one or more 
[WSO2 EI Tutorials](https://ei.docs.wso2.com/en/latest/micro-integrator/use-cases/integration-use-cases/).

### Example Use Case
In this example JSON data is sent to the application and then converted to the XML format using the messageType property.
Then the message payload is uploaded to the FTP folder.

### Set Up and Run the Example

1. Start WSO2 Integration Studio ([Installing WSO2 Integration Studio](https://ei.docs.wso2.com/en/latest/micro-integrator/develop/installing-WSO2-Integration-Studio/)).
2. In your menu in Studio, click the **File** menu. In the File menu select the **Import...** item.
3. In the Import window select the **Existing WSO2 Projects into workspace** under **WSO2** folder.
4. Browse and select the file path to the downloaded sample of this github project 
("upload-to-ftp-after-converting-json-to-xml" folder of the downloaded github repository).
5. Open the **UploadToFtpAfterConvertingJsonToXml.xml** under 
**upload-to-ftp-after-converting-json-to-xml/UploadToFtpAfterConvertingJsonToXml/src/main/synapse-config/api/UploadToFtpAfterConvertingJsonToXml.xml** directory. 
6. The **UploadToFtpAfterConvertingJsonToXml.xml** is the graphical view of the simple hello world service. Configure 
destination property accordingly.
7. Run the sample by right click on the **UploadToFtpAfterConvertingJsonToXmlCompositeApplication** under the main 
**upload-to-ftp-after-converting-json-to-xml** project and selecting **Export Project Artifacts and Run**.
8. Make a POST request using Postman to `http://localhost:8290/upload` with following JSON message body, and setting the 
`Content-Type` header to `application/json`:
```json
{
    "employees": {
        "employee": [
            {
                "name": "John",
                "lastName": "Doe",
                "addresses": {
                    "address": [
                        {
                            "street": "123 Main Street",
                            "zipCode": "111"
                        },
                        {
                            "street": "987 Cypress Avenue",
                            "zipCode": "222"
                        }
                    ]
                }
            },
            {
                "name": "Jane",
                "lastName": "Doe",
                "addresses": {
                    "address": [
                        {
                            "street": "345 Main Street",
                            "zipCode": "111"
                        },
                        {
                            "street": "654 Sunset Boulevard",
                            "zipCode": "333"
                        }
                    ]
                }
            }
        ]
    }
}
```
9. Verify that the file `miExample.xml` was uploaded to the `upload` folder on your FTP server.

### Go Further

* Learn more about [file connector](https://docs.wso2.com/display/ESBCONNECTORS/Working+with+the+File+Connector#WorkingwiththeFileConnector-append).
* Read more on [WSO2 connectors](https://docs.wso2.com/display/ESBCONNECTORS/WSO2+ESB+Connectors+Documentation)