# Notes

## Organizing Feature per File
Stay save one feature on one file. It might be tempting, for the sake of simplicity, to put everything in one file, or have one file per type; e.g. all controllers in one file, all components in another file, all services in a third file, and so on. This might seem to work well in the beginning, but as our application grows it becomes a burden to maintain. As we add more and more features, our files will get bigger and bigger and it will be difficult to navigate and find the code we are looking for.

Instead we should put each feature/entity in its own file. Each stand-alone controller will be defined in its own file, each component will be defined in its own file, etc.

## Organizing by Feature
So, now that we learned we should put everything in its own file, our app/ directory will soon be full with dozens of files and specs (remember we keep our unit test files next to the corresponding source code files). What's more important, logically related files will not be grouped together; it will be really difficult to locate all files related to a specific section of the application and make a change or fix a bug. Group our files into directory by *feature*.

```
app/
  phone-list/
    phone-list.component.js
    phone-list.component.spec.js
  app.js
```

## Using Modules
Each feature/section should declare its own module and all related entities should register themselves on that module.

```
app/
  phone-list/
    phone-list.module.js
    phone-list.component.js
    phone-list.component.spec.js
  app.module.js
```

### Notes
Note that files defining a module (i.e. .module.js) need to be included before other files that add features (e.g. components, controllers, services, filters) to that module.

## External Templates
Separate the template from *.js file using property ```templateUrl?``` on the component definition.

```
angular
    .module('phoneList')
    .component('phoneList', {
        templateUrl: 'phone-list/phone-list.template.html',
        controller:
```

## Filtering Repeaters
By a simple syntax ```| filter : 'query'```

Example
```
<li ng-repeat="phone in $ctrl.phones | filter:$ctrl.query">
```

## Data Binding
This is one of the core features in AngularJS. When the page loads, AngularJS binds the value of the input box to the data model variable specified with *ngModel* and keeps the two in sync.
