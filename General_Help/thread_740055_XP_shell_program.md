---
title: "XP shell program?"
date: 2008-03-30
forum: General Help
---

### Post by ticknubbs on 2008-03-30
I have seen a peer in on of my classes that runs Ubuntu on his laptop, as do I, On his he has some sort of shell program that lets him run Windows XP in Ubuntu so he can run both OS's at the same time. Anybody have an idea the name of the program such as this?

---

### Post by munkyeetr on 2008-03-30
[Virtual Box]("http://www.virtualbox.org/")
[VMWare]("http://www.vmware.com/")

---

### Post by ticknubbs on 2008-03-30
I have DL'ed virtual box but I cannot get ti to run.....do you know how to set it up?

---

### Post by trippinnik on 2008-03-30
First ```
sudo adduser <youruserName> vboxusers
```
then
```
sudo /etc/init.d/vboxdrv setup
```
then 
```
VirtualBox
```
After that you need to install a guest.  So you'll put your Windows CD / Other OS in the drive, click New, follow the wizard, then point virtual box to the Install Media and click Start.
you can look here for a howto:
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

---

### Post by ticknubbs on 2008-03-30
Thanks guys!

---

