---
title: "Need help installing compiz on hardy, new to ubuntu today"
date: 2008-05-02
forum: General Help
---

### Post by brianslater on 2008-05-02
I am new to ubuntu today, and sorry to ask such a noob question but how does one install compiz fusion on hardy heron, and how do I configure it?

---

### Post by sowelie on 2008-05-02
The first question is what kind of video card do you have?  Compiz is already installed you just need to enable it and install the configuration app, but let's make sure you are ready to do that before we try it.

---

### Post by alsamman on 2008-05-02
Go to System>Admin>Hardware Drivers and make sure your graphics card is enabled. Since compiz is installed by default all you need to install is the configuration manager and the tray icon if you want.
Type this in terminal:
```
 sudo apt-get install compizconfig-settings-manager
```
Once this is installed you will have something called Advanced Desktop Settings which you will be able to find under System>Preferences.
This will allow you to customize Compiz.
Then you can install the tray icon:
```
 sudo apt-get install fusion-icon
```
This will allow to you turn Compiz on/off very easily and if you want this tray icon to always load on startup then go to 
System>Preferences>Sessions, click Add, name: Compiz Tray Icon command: fusion-icon and then click OK
now you will have Compiz ready to go.

---

### Post by steveneddy on 2008-05-02
round compiz

---

### Post by alsamman on 2008-05-02
> **steveneddy said:**
> round compiz

cool how do you do that?

---

### Post by brianslater on 2008-05-02
Thanks guys, works perfectly!!!

---

### Post by Zorael on 2008-05-03
> **alsamman said:**
> cool how do you do that?
There should be a Cube Deformation plugin in ccsm (mentioned compizconfig-settings-manager package).

---

### Post by steveneddy on 2008-05-03
> **alsamman said:**
> cool how do you do that?

[Like this.]("http://ubuntuforums.org/showthread.php?t=763829&highlight=compiz-git")

Enjoy.

---

