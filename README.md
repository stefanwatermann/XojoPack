# XPack

A package manager software for XOJO components. 

<hr/>

This project aims to create a software solution which allows to establish a software package repository for XOJO based components (mainly Modules).

## Concept

This solution can be used to store/restore XOJO components (Modules) into/from a centraliazed repository. Components can be "imported" into existing XOJO projects from the central repository by **Copy&Paste**. By using this approach the XOJO IDE will integrate the component correctly and the project or IDE does not need to be reloaded or restarted.

A repository component is typically a regular XOJO Module. To make it visible to the package manager client (XPack) at least three Attributes have to be set on the Module.

![grafik](https://user-images.githubusercontent.com/73022584/199735219-fc5d4a2c-23a1-4ca1-bf44-a60149d2deb4.png)

Attribute names have to start with an at-sign (@), all Attribute values have to be strings (enclosed by double quotes).

| Attribute Name | Mandatory | Usage |
| --- | --- | --- |
| @Version | yes | Used to detect newer versions of the component by comparing repository with current project. |
| @Guid | yes | Global unique identifier for this component. New GUIDs can be created by the package manager client. |
| @Copyright | yes | Copyright of the author/owner of this component. |
| @Description | no | Describes the purpose of the component. |
| @Author | no | Developer name. |
| @Category | no | Can be used to categorize components. |
| @Depends | no | A comma-separated list of component GUIDs related to this component in some way.|


Please note that Attribute values can be set (or changed) within the XOJO IDE only and not by the package manager client later on.

## Conditions and Limitation

The package manager client is implemented as a standanlone desktop software and is not integrated into the XOJO IDE in any way. 

Because of the XOJO IDE it is not possible to automatically import components to a project. Therefor the Copy&Paste approach have to be used and the Client cannot automatically update existing components on a project.

A component have to be a XOJO Module. Other project items (Folder, Class, Window, etc.) can be included into the Module but cannot be used as a component directly.

The component repository has to be a folder on a (shared) drive to which the computer has access to. A (public) server component is not available so far.

## Current State

There is a client app avaliable, which allows to use a **locally hosted file-based repository** only. The app can be used to scan an exsiting XOJO project for Modules that are avaialble at the repository and checks the version of the Project Module against the repository version. It then allows to update Modules to a newer version by using the Copy&Paste approach.

![grafik](https://user-images.githubusercontent.com/73022584/199739505-b2a17389-eac0-47ab-b40a-d94571fdd998.png)



A server app is currently as early development version available.
