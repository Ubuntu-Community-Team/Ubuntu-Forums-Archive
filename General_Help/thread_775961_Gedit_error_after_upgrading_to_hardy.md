---
title: "Gedit error after upgrading to hardy"
date: 2008-04-30
forum: General Help
---

### Post by linuxrevo on 2008-04-30
I had Gusty and upgraded it to hardy. now when I run gedit I see this error:
$ gedit
Segmentation fault

Any idea?:(

---

### Post by forrestcupp on 2008-04-30
maybe try this
```
sudo dpkg-reconfigure gedit
```

---

### Post by linuxrevo on 2008-04-30
Nop!
I've tried it before. Didn't work. :(

---

### Post by linuxrevo on 2008-04-30
**[size="5"]help![/size]**

---

### Post by forrestcupp on 2008-04-30
Did you try purge removing it and installing again?
```
sudo apt-get --purge remove gedit
sudo apt-get install gedit
```

And is that the only app giving you that error?

---

### Post by linuxrevo on 2008-05-01
Ya mate! this is the only app. I've done Pure too.```
$ sudo apt-get --purge remove gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gedit* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 2802kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 188930 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gedit ...
Purging configuration files for gedit ...

```
```
sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gedit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/736kB of archives.
After this operation, 2748kB of additional disk space will be used.
Selecting previously deselected package gedit.
(Reading database ... 188860 files and directories currently installed.)
Unpacking gedit (from .../gedit_2.22.1-0ubuntu1_i386.deb) ...
Setting up gedit (2.22.1-0ubuntu1) ...
```
But didn't work :(

---

### Post by linuxrevo on 2008-05-01
Ya!
I just thought about Archive folder. I deleted Gedit and ubuntu-desk-top from there and downloaded a fresh one now gedit is working well :)

---

### Post by danwood76 on 2008-05-01
It could be some settings you have loaded for gedit.
Try removing the gedit config entries in your home folder.

I think they are:
~/.gnome2/gedit-2
~/.gnome2/gedit-metadata.xml

Obviously back them up before deleting them.

---

