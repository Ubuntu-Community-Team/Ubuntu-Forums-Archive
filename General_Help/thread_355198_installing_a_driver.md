---
title: "installing a driver?"
date: 2007-02-06
forum: General Help
---

### Post by mymuscle on 2007-02-06
I posted about this in the network forums but I dont know if I should post here or not.. but anyways....


I have a dell poweredge 1950 with dual nics that are integrated into the motherboard. 

It is a Broadcom NetXtreme II BCM5708 Gigabit Ethernet card. 


I have the driver burned onto cd from dell.com but how would I go about installing it to the system?


 the driver is in .tgz format.

---

### Post by Maestro23 on 2007-02-06
That's a tar file.  You can open it by using the "tar" command in a terminal.

You can type "man tar" at the prompt and get the syntax of the command.

---

### Post by mymuscle on 2007-02-07
i did what you said and there are only 2 files in there..... they are as follows:

bnx2-1.4.36b-5dkms.noarch.rpm
bnx2-1.4.36b-5dkms.src.rpm

now what?

---

### Post by Maestro23 on 2007-02-07
> **mymuscle said:**
> i did what you said and there are only 2 files in there..... they are as follows:

bnx2-1.4.36b-5dkms.noarch.rpm
bnx2-1.4.36b-5dkms.src.rpm

now what?

Ah, those are .rpm packages.  Check the link below on how to install.

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by mymuscle on 2007-02-07
is there another way to install?? it seems i need to download alien to get it to work, and my problem is that i cant download anything becuase its the nics drivers that i need to get working! haha

---

### Post by true_friend on 2007-02-07
u have to donwload it manually
or some other maching u have to use for this and copying packages in ur current machine.
u may use dialup etc..

---

### Post by Maestro23 on 2007-02-07
It might be on the Live CD.  Put the CD in your drive and try this:

> 
#sudo apt-cdrom add

#sudo apt-get update

#sudo apt-get install alien


**Again, not sure its on there, but worth a shot in your case.

---

### Post by mymuscle on 2007-02-07
:( not on the cd :( why does this have to be so compicated for me!!! its just a freaking network driver!!!! and it seems i cant get it to work for the life of me!

---

### Post by Polygon on 2007-02-07
most wireless chipsets are closed source, so the community has to write their own drivers, and since they are not open source, they are not included by default usually. or your chipset might be obscure and it might have drivers, but its not included

anyway, how are you posting on the forums now? you must have access to a computer that has internet access, so if you have a usb thumb drive or something, you can transfer the files over manually and double click it to install alien

Go to one of the links below depending on your distribution, scroll down to the bottom of the page,  to where it says "download alien". Click the "All" , choose a mirror, and download it to your desktop

[http://packages.ubuntu.com/edgy/admin/alien](http://packages.ubuntu.com/edgy/admin/alien) <- If you use edgy

[http://packages.ubuntu.com/dapper/admin/alien](http://packages.ubuntu.com/dapper/admin/alien) <- if you use dapper

then using your usb key, simply transfer it over to your ubuntu computer, and double click it and install it, then try to install your network driver using alien.

post here if you have trouble with the driver still!

---

