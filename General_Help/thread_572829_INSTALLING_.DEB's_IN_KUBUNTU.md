---
title: "INSTALLING .DEB's IN KUBUNTU????"
date: 2007-10-10
forum: General Help
---

### Post by gdaman on 2007-10-10
I switched from Ubuntu to Kubuntu and the only one thing that really hate is that .deb installation files are opened in ARK, instead to run installation gui like it was in Ubuntu. Also tried right click-->Kubuntu Package Menu-->Install Package... and installed with errors, so it didn't worked.... So How to INSTALL DEBs In Kubuntu????:mad:

---

### Post by dabl on 2007-10-10
OK -- something is wrong with this picture  :confused:

Download a .deb file to your Kubuntu desktop.  Right-click on the file, choose "Open With > Gdebi Package Installer" and it will install.  That's it.  Unless you're trying to put 32-bit apps on a 64-bit platform, or something hokey like that.  :)

---

### Post by abn91c on 2007-10-10
> **gdaman said:**
> I switched from Ubuntu to Kubuntu and the only one thing that really hate is that .deb installation files are opened in ARK, instead to run installation gui like it was in Ubuntu. Also tried right click-->Kubuntu Package Menu-->Install Package... and installed with errors, so it didn't worked.... So How to INSTALL DEBs In Kubuntu????:mad:

you probably had some file dependencies and you got errors. It usually tells you with the error what command to use to fix it.  Also go to a terminal and try sudo apt-get check or sudo apt-get clean, most of the time it will telll you what the missing files are and what command to use. MAke sure when you right click the deb files Adept manager is not running.

---

### Post by the yawner on 2007-10-10
On Feisty, there is no Gdebi for Kubuntu but you could add it in Synaptics. Kubuntu Gutsy ships out with Gdebi.

---

### Post by finferflu on 2007-10-10
I still think the command line is the best option. 

```
sudo dpkg -i /path/to/file.deb
```

this way you will have some very useful output, and won't need any Ubuntu/Kubuntu related problems ;)

---

### Post by nilpill on 2007-10-10
I agree with abn91c, if you're just seeing errors in the install, it's most likely just because you're missing some dependencies of whatever it is you're trying to install.

---

### Post by FuturePilot on 2007-10-10
The Install Package feature in the right click menu doesn't take care of dependencies. You need to run this
```
sudo apt-get install -f
```

---

