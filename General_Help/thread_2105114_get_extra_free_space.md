---
title: "get extra free space"
date: 2013-01-15
forum: General Help
---

### Post by marchelloUA on 2013-01-15
Hi all, 

how do I get to know what unuseful packages I can uninstall to get some extra free space?

---

### Post by howefield on 2013-01-15
Browse here whilst you are waiting for a reply :-)

[http://ubuntuforums.org/showthread.php?t=1889034](http://ubuntuforums.org/showthread.php?t=1889034)

---

### Post by blackbird34 on 2013-01-15
To get extra free space Bleachbit is a very good tool.
[https://apps.ubuntu.com/cat/applications/precise/bleachbit/](https://apps.ubuntu.com/cat/applications/precise/bleachbit/)

It is available in the Software centre or else you can run the command
 
```
sudo apt-get install bleachbit
```

The reviews say everything you need to know.

---

### Post by ibjsb4 on 2013-01-15
+1 to BleachBit; an easy way to gain space.  A tip:  Do not use any BB box you check that has a pop-up with a warning.  Also watch what you check in the browser's boxes.

You can also take a look at recommended packages.  These packages are not necessary for default operation.  An example would be libreoffice.  Do you need/use all those packages?  Bluez (bluetooth), do you use that?

[http://packages.ubuntu.com/quantal/kubuntu-desktop](http://packages.ubuntu.com/quantal/kubuntu-desktop)

---

### Post by marchelloUA on 2013-01-15
[ibjsb4]("http://ubuntuforums.org/member.php?u=1729120"), 

yea, libreoffice is not useful for me, I'd rather install some simple kind of notepad instead. 

Sure I will look through programs that are visible in "X-Windows Start menu". But what about those I can't see in this X menu?

---

### Post by ibjsb4 on 2013-01-15
ALL packages are listed in the above link.  Kubuntu-desktop is the top level.  Click on any package, it will lead to more packages and in turn those packages will lead to more packages.  Its the dependencies of dependencies of dependencies and so on.  So by removing the top level, you remove many packages.

Use the autoremove command

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

---

