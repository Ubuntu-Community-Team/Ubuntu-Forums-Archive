---
title: "Clearing HD space after aborted VMware installations....."
date: 2007-07-14
forum: General Help
---

### Post by elcartero on 2007-07-14
is proving to be a problem!
In two separate aborted attempts at creating a VM I have allocated a total of 12G space on my Ubuntu 7.04 partition leaving me very short of space for expansion. I have uninstalled and purged the application but am unable to discover how to recover the disk space used.
Any advice would be much appreciated as I now wish to re-install VMware server and create a new VM.
Thank you

---

### Post by sefs on 2007-07-14
Look into your home folder for a directory called vmware i.e /home/yourusername/vmware

In this directory is were the OS related files for vmware are kept ... if you see any then right click on the folders to see if they add up to your 12 GB of space.  If so then these are what you have to get rid of, and you are completely sure they are not VMWare OS installations that you need.

---

### Post by HermanAB on 2007-07-14
Yup, I always set VMware to use a base directory where I can easily find things again.  Then backing up or deleting appliances is as easy as making a tar ball and deleting a directory.

---

### Post by elcartero on 2007-07-15
sefs and HermanAB.......many thanks for your help.....

---

