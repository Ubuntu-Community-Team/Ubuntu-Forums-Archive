---
title: "hal-storage-fixed-mount-all-options refused uid 999"
date: 2008-03-06
forum: General Help
---

### Post by rphil2008 on 2008-03-06
Hi guys, I am also trying out Kubuntu 7.1.  I could not navigate to my Windows partition and the other NTFS partition. In Ubuntu and Edubuntu 7.1 this is not a problem as I have found out lately. But in Kubuntu 7.1 and other KDE distros I tried, I get this error when I click on those NTFS partitions:

hal-storage-fixed-mount-all-options refused uid 999

I want to access those partitions but I dont know how. Thanks for your help.

---

### Post by rphil2008 on 2008-03-07
GOT IT! Finally. 

Score 10 for the book Ubuntu Linux Toolbox! No, Im not connected in any way to the publishers/authors. It turns out the NTFS partitions are not mounted by default in Kubuntu 7.1. I checked with Linux Mint 4 KDE and the behavior is the same. The book provided instructions on how to mount it using the command line.

sudo mkdir /mnt/<any name> 
sudo mount /dev/sda<device number> /mnt/<the name above>

ex:

sudo mkdir /mnt/mountain
sudo mount /dev/sda5 /mnt/mountain

The above command will unlock all permissions to the device (sda5.) You can then read, write, and execute on the subject device- in this case, my NTFS partition containing data.

There are other options to the mount command to limit the level of access. I'll leave you to it...

I deserve a break. The coffee machine is waiting=)

---

