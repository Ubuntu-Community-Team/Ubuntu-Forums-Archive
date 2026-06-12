---
title: "help installing visual studio"
date: 2007-11-22
forum: General Help
---

### Post by Diabolis on 2007-11-22
I want to install vmware and then xp so I can use visual studio. I downloaded the visual studio 2008 .iso file from microsoft, but it's too big to be burned into a CD and my laptop doesn't have a DVD burner. Is there any application that would let me mount the .iso file so I can make the installation directly from it?

Someone gave an already burned visual studio CD, but I can't use it. When the computer tries to read it, it only show one readme.txt file that says the following:
```
This disc contains a "UDF" file system and requires an operating system

that supports the ISO-13346 "UDF" file system specification.
```

Anyone knows how could I install visual studio?

---

### Post by thetimekeeper on 2007-11-23
If you use VMware, there should be an option to mount a iso as a cd drive within the virtual machine. I don't know which VMware product you're using, but my VMware server has it.

---

### Post by mock on 2008-05-24
you need to pass an udf argument

sudo mkdir /media/VSDISC


sudo mount VSSETUP.iso -t /media/VSDISC/ -o loop

where VSSETUP.iso is the iso

then i think (! as i don't know) you have to

sudo unmount /media/VSDIC

to unmount it.

But i don't think it will work to install it (i have tried myself) as wine will complains about some spaceissues (and perpaps permissions)

If anyone could help i would be grateful.

---

### Post by KOld Iron on 2008-05-24
> **thetimekeeper said:**
> If you use VMware, there should be an option to mount a iso as a cd drive within the virtual machine. I don't know which VMware product you're using, but my VMware server has it.

I think every product of VMWare has that (and VirtualBox by the way, too), because that's the usual way to install the Guest Utilities, i.e. by mounting an ISO and running the setup of the Guest Utilities from it. So, just copy your ISO to some folder of your Linux installation, configure your VMWare machine to use the ISO in the CD drive and start your virtual machine. After logging on to your virtual XP, the CD drive will show your ISO as a regular CD/DVD. That's it.

---

