![Pub](https://img.shields.io/pub/v/slidy?color=orange)
[![GitHub stars](https://img.shields.io/github/stars/Flutterando/slidy?color=yellow)](https://github.com/Flutterando/slidy/stargazers)
[![Telegram](https://img.shields.io/badge/telegram-flutterando-blue)](https://t.me/flutterando)

[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Dart%20CI/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Example%20Android/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Example%20iOS/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Packages/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)
[![Actions Status](https://github.com/AlvaroVasconcelos/slidy/workflows/Tests/badge.svg)](https://github.com/AlvaroVasconcelos/slidy/workflows/actions)


[Acesse a documentação em Português-Brasil](README-PT.md)

# Slidy
CLI package manager and template generator for Flutter. Generate Modules, Pages, Widgets, BLoCs, Controllers and tests.

Slidy supports rxBLoC, flutter_bloc and mobx.

# Why should I use?

Slidy's goal is to help you structure your project in a standardized way. Organizing your app in **Modules** formed by pages, repositories, widgets, BloCs, and also create unit tests automatically. The Module gives you a easier way to inject dependencies and blocs, including automatic dispose. Also helps you installing the dependencies and packages, updating and removing them. The best is that you can do all of this running a single command.

# Motivations

We realized that the project pattern absence is affecting the productivity of most developers, so we're proposing a development pattern along with a tool that imitates NPM (NodeJS) functionality as well as template generation capabilities (similar to Scaffold ).

# About the Proposed Pattern

The structure that slidy offers you, it's similar to MVC, where a page keeps it's own **business logic classes(BloC)**. 

We recommend you to use [bloc_pattern](https://pub.dev/packages/bloc_pattern) when structuring with slidy. It offers you the **module structure**(extending the ModuleWidget) and dependency/bloc injection, or you will probably get an error. 

To understand **bloc_pattern package**, take a look at the [README](https://github.com/jacobaraujo7/bloc-pattern/blob/master/README.md).

We also use the **Repository Pattern**, so the folder structure it's organized in **local modules** and a **global module**. The dependencies(repositories, BloCs, models, etc) can be accessed throughout the application.

Sample folder structure generated by **slidy**:

![Folder example](https://github.com/Flutterando/slidy/blob/master/screenshots/folderw.png?raw=true)

## Installation


1. Activate the slidy using the pub:
    ```
    flutter pub global activate slidy
    ```
2. Type ` slidy --version` to make sure everything is working properly. This command should return the installed version.


## Commands: 

### upgrade:

Updates slidy's version:

```  
slidy upgrade
```   

### start:

Create the basic structure of your project (make sure that your "lib" folder it's empty).

```  
slidy start
```       

Then choose your provider:

![Folder example](/screenshots/choose_provider.PNG?raw=true)

Then choose your State Manager:

Mobx

![Folder example](/screenshots/choose_state_management_mobx.PNG?raw=true)

And you will get this Structure:

![Folder example](/screenshots/start_cmd.png?raw=true)



Flutter Bloc:

![Folder example](/screenshots/choose_state_management_flutter_bloc.PNG?raw=true)

And you will get this Structure:

![Folder example](/screenshots/start_cmd_flutter_bloc.PNG?raw=true)


Bloc With RxDart

![Folder example](/screenshots/choose_state_management_rxdart.PNG?raw=true)

And you will get this Structure:

![Folder example](/screenshots/start_cmd_rxdart.PNG?raw=true)



If you have the flutter_bloc or flutter_mobx package in pubspec, the generation of pages, widgets, and bloc defaults to the installed manager default.

#### Options
The command allows to specify provider and state manager using the following options:
* Provider:
```
-p <provider_name>

Options:
flutter_modular / bloc_pattern

Example:
slidy start -p flutter_modular
```
* State manager: 
```
-s <state_manager_name>

Options: 
mobx / flutter_bloc / rxdart
Example:
slidy start -s mobx
```
* Provider and state manager:
```
slidy start -p flutter_modular -s mobx
```
This command asks for permission to erase lib folder. If you don't want to see the warning, type the -e (erase) flag:
```
slidy start -p flutter_modular -s mobx -e
```

### run:

Runs the scripts in pubspec.yaml:

```  
slidy run open_folder
```    

![Folder example](/screenshots/scripts.png?raw=true)

### install:

**Installs or update the packages in dependencies:** 

![Folder example](/screenshots/dependencies.png?raw=true)

```
slidy install rxdart dio bloc_pattern
``` 

or you can just use the **i** command (both are the same)

```
slidy i rxdart dio bloc_pattern
```

**Install packages as dev_dependency:**

```
slidy i mockito --dev
``` 

![Folder example](/screenshots/dev_d.png?raw=true)

### uninstall:

Removes a package
 ```
 slidy uninstall dio 
 ```
You can also remove a **dev_dependency** using the flag --dev


### generate:

Creates a module, page, widget or repository including its BloC class.

**NOTE:** You can replace "g" with "generate" command. 

Creates a new **module**:

``` 
slidy g module folder_name
``` 
or
``` 
slidy g m folder_name
``` 

![Folder example](/screenshots/module_cmd.png?raw=true)

**NOTE:** You can create a "Complete Module" with Module, Page, Bloc/Controller, tests for Page and for Bloc/Controller using the flag **-c**


Creates a new **page** + BloC:

```
slidy g page folder_name/pages
``` 
or
```
slidy g p folder_name/pages
``` 

Creates a new **widget** + BloC:

```
slidy g widget folder_name/widgets
``` 
or
```
slidy g w folder_name/widgets
``` 

**NOTE:** You can create a page or widget using its respective BLoC using the flag **-b**


Create a new **repository**
```
slidy g r folder_name/repositories
``` 

Create a new **service**
```
slidy g s folder_name/services
``` 

Create a new **model**
```
slidy g mm folder_name/model
``` 

You can also use "repository" in "r"'s place, but it will have the same function.

![Folder example](/screenshots/structure.png?raw=true)


## Unit Tests:

Generate **unit tests** on the test folder for you.

```
slidy test folder_name/
``` 

## Common errors:

**Windows:** 

  ![Folder example](/screenshots/error_windows_install.jpg?raw=true)

  If you got this error when trying to run the ```pub global activate slidy```, then you will have to set the environment variables manually:

  * In windows search, write:  ```Edit System Variables```

  ![Folder example](/screenshots/step1.png?raw=true)

  * Then click at ```Environment Variables```

  ![Folder example](/screenshots/step2.png?raw=true)

  * Go to ```Path```

  ![Folder example](/screenshots/step3.png?raw=true)

  * Then click in New and add the path that appeared on your console.

  ![Folder example](/screenshots/step4.png?raw=true)

If you have any doubt about setting up the system variables, watch [this](https://www.youtube.com/watch?v=bEroNNzqlF4) video.


For more details join our [Telegram Group Flutterando](https://t.me/flutterando)

