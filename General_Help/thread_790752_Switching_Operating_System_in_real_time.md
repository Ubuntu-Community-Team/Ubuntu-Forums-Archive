---
title: "Switching Operating System in real time"
date: 2008-05-11
forum: General Help
---

### Post by zorocke on 2008-05-11
Hey, I am probably crazy for even wondering if this is possible, but is there a way I can switch between Windows and Linux in "real time". Like without needing to reboot because I develop on both, but rebooting so often is a real pain.

---

### Post by bite on 2008-05-11
Yes, if you virtualize one of the two.

---

### Post by ghost_ryder35 on 2008-05-11
> **bite said:**
> Yes, if you virtualize one of the two.
yep, check out vmware workstation or virtual box

---

### Post by zorocke on 2008-05-11
I've been looking into virtual box, and from what i read i would need to install a new copy of windows under the virtual box. But is there a way to run my current installation of windows under Virtual Box?

---

### Post by Lord Xeb on 2008-05-11
I have heard somewhere that you can migrate your Windows install to Virtual box, but I am not sure of it.


Edit: I found something that might be of use to you. It is in attached to this post. I got it from the virtualbox website.

here is the link as well (you might want to check the link first): [Migrate Windows]("http://www.virtualbox.org/wiki/Migrate_Windows")

---

### Post by ghost_ryder35 on 2008-05-11
> **zorocke said:**
> I've been looking into virtual box, and from what i read i would need to install a new copy of windows under the virtual box. But is there a way to run my current installation of windows under Virtual Box?
you can create a backup image of it and then restore it in the virtual machine :)

---

### Post by ghost_ryder35 on 2008-05-11
there is also an option in vmware workstation to create a cirtual machine from the host machine.  so if you run vmware workstation in windows you can create a virtual machine of it and then use it in ubuntu

---

### Post by Lord Xeb on 2008-05-11
Interesting.... I wish I had know that before I *****ed my system (I reformated without knowing how to fix my boot) :/

---

### Post by zorocke on 2008-05-11
> **ghost_ryder35 said:**
> you can create a backup image of it and then restore it in the virtual machine :)

Any one know of any easy ways of creating this backup image?

---

### Post by zorocke on 2008-05-11
Okay, I have figured out how to create the image, and load it in virtualbox. I am having a problem though... I created the image from my current XP install, so when i try to start the virtual machine, the grub loader returns an error. 

Is there a way I can temporally set windows back to it's default boot loader and then create a new image.

---

### Post by damis648 on 2008-05-11
If you have an ISO of the original windows disc, mount it in the virtual machine and boot it. When you get to the installer, instruct it to repair the MBR.

EDIT: you dont even need an ISO, just mount the physical drive if you have the disc.

---

### Post by zorocke on 2008-05-11
:( I do not have the original disc.

---

### Post by AusIV4 on 2008-05-11
Take a look at [andlinux]("http://www.andlinux.org/"). It's supposed to let you run Ubuntu within Windows more efficiently than virtualization by porting the Linux kernel as a Windows application.

---

### Post by damis648 on 2008-05-11
Ah that might be a problem. Try and google for an MBR repair disc.

---

### Post by damis648 on 2008-05-11
Maybe this will help: [http://bootmaster.filerecovery.biz/recover_mbr.html](http://bootmaster.filerecovery.biz/recover_mbr.html)

---

### Post by damis648 on 2008-05-11
By the way, thanks for the Andlinux post. Although i do have ubuntu installed, this looks interesting. Reminds me of when i saw KDE running on Mac OS X. I am about to reboot and try it ;).

---

### Post by zorocke on 2008-05-11
> **AusIV4 said:**
> Take a look at [andlinux]("http://www.andlinux.org/"). It's supposed to let you run Ubuntu within Windows more efficiently than virtualization by porting the Linux kernel as a Windows application.

look cool, but I believe what I really want to do is run windows in linux because mainly what i use is linux with some windows on the side. So this wont work.

---

### Post by zorocke on 2008-05-11
> Maybe this will help: [http://bootmaster.filerecovery.biz/recover_mbr.html](http://bootmaster.filerecovery.biz/recover_mbr.html)

If i use this will I be able to easily restore grub later?

---

### Post by inportb on 2008-05-11
> **AusIV4 said:**
> Take a look at [andlinux]("http://www.andlinux.org/"). It's supposed to let you run Ubuntu within Windows more efficiently than virtualization by porting the Linux kernel as a Windows application.

Looks great. But really, it's a kind of virtualization ;p

---

### Post by damis648 on 2008-05-11
Well are you not trying to restore the MBR in the VM? WHy would you need to restore the grub if all you are doing is booting windows? Just boot the VM with this disc and restore the Virtual MBR.

---

