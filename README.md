# Basic CRUD App with Angular 7.0 and Spring Boot 2.1
 
This example app shows how to build a basic CRUD app with Spring Boot 2.1, Spring Data, and Angular 7.0.

Please read [Build a Basic CRUD App with Angular 7.0 and Spring Boot 2.1](https://developer.okta.com/blog/2018/08/22/basic-crud-angular-7-and-spring-boot-2) to see how this app was created.

**Prerequisites:** [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and [Node.js](https://nodejs.org/). For Java 10+, you'll need to change the `java.version` property and `jaxb-api` as a dependency. See Josh Long's [spring-boot-and-java-10](https://github.com/joshlong/spring-boot-and-java-10) project on GitHub for more information.

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example application, run the following commands:

```bash
git clone https://github.com/oktadeveloper/okta-spring-boot-2-angular-7-example.git
cd okta-spring-boot-2-angular-7-example
```

This will get a copy of the project installed locally. To install all of its dependencies and start each app, follow the instructions below.

To run the server, cd into the `server` folder and run:
 
```bash
./mvnw spring-boot:run
```

To run the client, cd into the `client` folder and run:
 
```bash
npm install && npm start
```

### Create a New OIDC App in Okta

To create a new OIDC app on Okta:

1. Log in to your developer account, navigate to **Applications**, and click on **Add Application**.
3. Select **Single-Page App** and click **Next**. 
4. Give the application a name, change all instances of `localhost:8080` to `localhost:4200` and click **Done**.

#### Server Configuration

Set your domain and copy the `clientId` into `server/src/main/resources/application.yml`. 

**NOTE:** The value of `{yourOktaDomain}` should be something like `dev-123456.oktapreview`. Make sure you don't include `-admin` in the value!

```yaml
okta:
  oauth2:
    client-id: {clientId}
    issuer: https://{yourOktaDomain}/oauth2/default
```

#### Client Configuration

For the client, set the `issuer` and copy the `clientId` into `client/src/app/app.module.ts`.

```typescript
const config = {
  issuer: 'https://{yourOktaDomain}/oauth2/default',
  redirectUri: window.location.origin + '/implicit/callback',
  clientId: '{clientId}'
};
```

## Links

This example uses the following open source libraries from Okta:

* [Okta Spring Boot Starter](https://github.com/okta/okta-spring-boot)
* [Okta Angular SDK](https://github.com/okta/okta-oidc-js/tree/master/packages/okta-angular)

## Help

Please post any questions as comments on the [blog post](https://developer.okta.com/blog/2018/08/22/basic-crud-angular-7-and-spring-boot-2), or visit our [Okta Developer Forums](https://devforum.okta.com/). You can also email developers@okta.com if would like to create a support ticket.

## License

Apache 2.0, see [LICENSE](LICENSE).
