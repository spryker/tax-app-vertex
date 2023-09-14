# tax-app-vertex
This is the example of project side integration with Spryker and ACP Vertex app.
This code can be used as a starting point or for a demo.

If you want to add specific Vertex Codes for a specific products, etc., you have to add JSON file with path `{projectRootDir}/data/import/vertex_codes.json` with contents like this:

```json

{
  "customerCodes": {
    "DE--1": "VC1",
    "DE--2": "VC2",
    "DE--3": "VC3"
  },
  "productCodes": {
    "001_25904006": "VP1",
    "002_25904004": "VP2",
    "003_26138343": "VP3"
  },
  "productOptionCodes": {
    "OP_1_year_warranty": "VP1",
    "OP_2_year_warranty": "VP2",
    "OP_3_year_warranty": "VP3",
    "OP_insurance": "VP4"
  },
  "expenseCodes": {
    "TYPE|NAME|MERCHANT_REFERENCE": "VE",
    "TYPE1|NAME|MERCHANT_REFERENCE1": "VE1"
  },
  "exemptionsCertificates": {
    "DE--1": "VES1",
    "DE--2": "VES2",
    "DE--3": "VES3"
  }
}

```

In this case values which are specified in this file will override original default values in package. 
The logic will work in 2 ways:
1. If you've provided custom mapping. For example you are specified `"DE--1": "VC1"` in customerCodes section (which means customer with customer referece `DE--1` should have vertex xode `VC1`). If customer will be found in the cart or order it will be populated wuth this code. If not it will be populated with random Vertex Code you've provided.
2. If you've not provided cusomt mappins. It will work the same but will use internal mapping which you could find in `Spryker/Zed/TaxAppVertex/Communication/VertexCodeMapper.php`.
