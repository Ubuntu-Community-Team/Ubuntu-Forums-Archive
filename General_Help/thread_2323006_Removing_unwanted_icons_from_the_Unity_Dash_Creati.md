---
title: "Removing unwanted icons from the Unity Dash/ Creating new Application shortcuts"
date: 2016-05-02
forum: General Help
---

### Post by pst007x on 2016-05-02
This seems to be a common issue. Unfortunately Ubuntu does not come with a MENU editor, so editing the Applications list is difficult for the average user.

Removing unwanted icons.

First I uninstalled the application, then I deleted all references from the following folder:

    /usr/share/applications
    /usr/local/share/applications
    ~/.local/share/applications

Rebooted....but never resolved my issue.

So installed this [MENU editor]("http://www.webupd8.org/2013/06/ezame-new-menu-editor-for-unity.html"):

    sudo add-apt-repository ppa:caldas-lopes/ppa
    sudo apt-get update
    sudo apt-get install ezame

and delete unwanted icons.

The MENU editor allows for removing and adding new Application shortcuts,

---

### Post by deadflowr on 2016-05-02
System Settings >> Security and Privacy >> Files and Applications >> click on the clear usage button.
Select a time frame and then OK.

This will clear all recent activity for the dash, AS WELL AS all applications such as the recently opened sections for gedit and Files.
If you wish to still have those, then in the main window you need to add those to the exclude list by press the plus (+) sign in the bottom left corner
Select add application and select the application from the dropdown list.

---

