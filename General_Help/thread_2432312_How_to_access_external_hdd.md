---
title: "How to access external hdd"
date: 2019-11-30
forum: General Help
---

### Post by antee on 2019-11-30
Hello,
 I cannot access home partition (now/media/user name/folder name) on my usb hdd which has Ubuntu gnome 16.04 and login password. I have Ubuntu 19.10.  

 Home partition on usb hdd has two files:
 Access-Your-Private-Data.desktop and readme.txt
 
 Content of readme.txt is:
 ```
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.
 From the graphical desktop, click on:
  "Access Your Private Data"
or
 From the command line, run:
  ecryptfs-mount-private

 Click on "Access Your Private Data" opens it in text editor
 and
 ecryptfs-mount-private
 shows error:
 Encrypted private directory is not setup properly
```
 
 If i run
 sudo ecryptfs-recover-private /media/user name/folder name  
 i get
 Success!  Private data mounted at [/tmp/ecryptfs.ebWvc6Qz]
 and if i go to
 admin:///tmp/ecryptfs.ebWvc6Qz
 i end up at the same file:
 Access-Your-Private-Data.desktop
 which i can open in tex editor.

 What application should i use to open it.
I am not very familiar with Linux so any help is greatly appreciated.

 Thank you
 antee

---

### Post by deadflowr on 2019-11-30
Files in the /tmp directory should be viewable without root/sudo/admin just by opening the location in Files, the file manager.

---

