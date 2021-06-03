# lambda-up
Modules to level up writing AWS Lambda Functions


- `lambda-local-apig` Lambda local development for API Gateway
- `lambda-doc-gen`  Generate OpenAPI Documentation programatically for your handlers
- `lambda-controller` Inspiration from https://github.com/dotmh/lambda-controller/blame/master/index.js using classes can add some predictability to stuff like documentation generation, request and response input validation
- `ts-lambda-dev` like `ts-node` but for lambda functions


## Notes

Lambda controller uses classes, which can make definitions predictable.  https://github.com/dotmh/lambda-controller
together with figuring out what `_@epiphone` is doing here https://github.com/epiphone/routing-controllers-openapi/blob/master/src/generateSpec.ts  This would provide a proper in-codegen doc generating experience, but maybe we will skip this for now, since it’s relatively complex coupled with utilities for developing locally.

#### Method Two

Manually writing jsdoc annotations on handlers could do the trick coupled with some type definitions see  https://github.com/Surnet/swagger-jsdoc/blob/master/examples/yaml-anchors-aliases/x-amazon-apigateway-integrations.yaml

Optionally we could automate generating /#components/definition Files using an utility like https://github.com/grantila/typeconv/ which is pretty much silver bullet for anything TS to YAML or JSON 

Method Three

Find a hack around the implementation by GROOT for express and re-mount it for execution in a lambda’s path instead, should work with `lambda-local-apig` and hook into the server method https://github.com/pgroot/express-swagger-generator


## Requirements
- can use the onion style middleware provided by middy
- can validation request and response object using `class-validator`
- can develop with typescript
- can generate documentation for the handlers based on annotations, decorators or comments within the code
- can run locally without the need for AWS SAM or AWS credentials.... (ps: might want to wrap `lambda-local-apig` into `ts-lambda-dev`) and provide methods to choose the event mock to use, from APIG, or Alexa, or SNS etc.
