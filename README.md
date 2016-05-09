# angular-jwt-auth
Mix [auth0/angular-jwt](https://github.com/auth0/angular-jwt) & [witoldsz/angular-http-auth/](https://github.com/witoldsz/angular-http-auth/) to get automatic auth when response code is 401.

## Documentation

### Custom methods

You can override the `credentialsService` methods.

```js
angular.module('angular-jwt-auth', ['angular-jwt', 'angular-jwt-auth.credentials'])
.config(function($httpProvider, jwtInterceptorProvider, credentialsServiceProvider) {

  // Please note we're annotating the function so that the $injector works when the file is minified

  credentialsServiceProvider.saveToken = ['localStorageService', function(localStorageService) {
    localStorageService.set('auth.jwt_token', this); // "this" is set by $injector, https://docs.angularjs.org/api/auto/service/$injector
  }];

});
```