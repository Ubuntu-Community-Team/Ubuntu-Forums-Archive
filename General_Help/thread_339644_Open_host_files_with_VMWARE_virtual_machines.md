---
title: "Open host files with VMWARE virtual machines"
date: 2007-01-16
forum: General Help
---

### Post by ghepardo on 2007-01-16
Can I open the files in my pc through a vmware virtual machine? 
My situation is the seguent:
I have kubuntu and I installed winxp in a vmware virtual machine. Can I, from the winxp virtual machine, open / transfer files to my home directory for example?

---

### Post by andreas64 on 2007-01-16
Yes, you can. Just enable the "Shared Folders" in your VM settings and point it to your home-folder.

Andreas

---

### Post by gwpritch on 2007-01-16
Its not quite that simple, you are going to have to configure samba as you are actually setting up a virtual network.
This thread makes it pretty simple:

[http://ubuntuforums.org/showthread.php?t=296668]("http://ubuntuforums.org/showthread.php?t=296668")

---

### Post by andreas64 on 2007-01-17
No, that's not right.
You don't have to configure samba.

VMWare does it for you automatically if you enable the Shared Folders for your virtual machine.
After that, you can access the folders through the windows-network-neighborhood.

Andreas

---

### Post by ghepardo on 2007-01-17
> **andreas64 said:**
> No, that's not right.
You don't have to configure samba.

VMWare does it for you automatically if you enable the Shared Folders for your virtual machine.
After that, you can access the folders through the windows-network-neighborhood.

Andreas

How can I enable it? Where is that?
I used this guide:
[http://www.vmware.com/support/ws4/doc/running_sharefold_ws.html](http://www.vmware.com/support/ws4/doc/running_sharefold_ws.html)
but in the options tab I don't have the "shared folders" option. Why?

---

### Post by andreas64 on 2007-01-18
Hi,

Open the virtual machine and then choose VM -> Settings -> Options -> Shared Folders

Andreas

---

### Post by ghepardo on 2007-01-18
I did it but I dont have the "shared folder" in the options tab.

---

### Post by gwpritch on 2007-01-18
Take my advice man...follow the thread I gave you earlier.

---

### Post by derjames on 2007-01-18
> **andreas64 said:**
> Yes, you can. Just enable the "Shared Folders" in your VM settings and point it to your home-folder.

Andreas

You can do this if you have VMware Workstation edition....

If you have VMware server edition then follow **gwpritch** advice

If you have VMware player... I think is not possible

---

### Post by gwpritch on 2007-01-18
same thing works with vmplayer assuming the virtual machine was originally built with ethernet support.

---

### Post by ghepardo on 2007-01-18
is the workstation edition free for personal use?

---

### Post by derjames on 2007-01-20
No it is not. For VMware server workstation you've got to pay a licence fee...

VMware player and Vmware Server are free to use...

I've got VMware Server and what I am doing to transfer files between the Virtual Machine and the Host is to use an external USB drive, I simply swith to the drive back and forth every time is needed, I think is the simplest solution... otherwise you have to install and configure SAMBA (which is not difficult) or pay for VMware workstation...

cheers

---

### Post by ghepardo on 2007-01-20
Thank you.

---

### Post by derjames on 2007-01-20
ghepardo, if you really want this feature, consider VirtualBox which is free and OpenSource and is giving you the feature to share folders,  I haven't tried yet, but it seems to be a good option... please read for the full set of features:

[http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)

hope this helps.

cheers

---

### Post by ghepardo on 2007-01-21
Thank you a lot, I will check this out as soon as I have time. Thank you.

---

