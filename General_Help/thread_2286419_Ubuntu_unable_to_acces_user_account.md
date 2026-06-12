---
title: "Ubuntu unable to acces user account"
date: 2015-07-11
forum: General Help
---

### Post by dsx2 on 2015-07-11
hi all 

i tried yesterday to download virtual box on my ubuntu14.04 from the VB website to get a specific version so i got a .deb so the download started from the software center, the icon start to bug when i restarted the left panel was missing and only the document  previously in the desktop was shown .

I coudnt only open the tty (ctrl alt f1) 
sudo apt-get autoremove vritualbox, 
didnt return any result except nothing except  20 software  to remove i clicked  yes and any programs was removed after that i was unable to acces any user account on my ubuntu ! When i enter the correct password it retun me to the same prompt to enter it again ..

 i was suggeted to do this 
```
sudo apt-get remove --purge virtualbox
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```


root prompt in safe mode titled 
 (recovrey menu) file system state read only  return this :
i got this message after the command apt-get remove --purge virtualbox

```
W:not using locking for read only lock file /var/lib/dpkg/lock
E:unable to write to /var/cache/apt
E:the package list or status could not be parsed or opened
even with mount --all same message after the remove --purge command 
```

 im running ubuntu in a dual boot so my rescue mode is something like that 



The grub menu (Gnu Grub verion 2.02...)
```
  ubuntu
  advanced option for ubuntu 
  memory test (memory test 86)
  memory test (memory test 86+serial...
```

 Once i get to advanced option for ubuntu i end up with this :
```

 ubuntu with linux3.16.0-34 generic 
 ubuntu with linux3.16.0-34 generic (recovery mode)
 ubuntu with linux 3.16.0-30
 ubuntu with linux 3.16.0-30 ( recovery mode)

```
then i choose 3.16.0-34 [recovery mode] (file system state :read only)

```
  resume
  clean: try to make free space
  dpkg:  repair broken package
  failsafe:  run in a fail safe graphic mode 
  fsck: check all file system 
  grub: update grub boot loader 
  network  :enable networking 
  root: drop to root shell prompt 
  system summary: system summary

```

Any clue about what going wrong and how to repair corrupted\missing files on / ???

---

### Post by QIII on 2015-07-12
Moved to ***General Help***.

The Ubuntu, Linux and OS Chat area is not a support area.

Also, please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

