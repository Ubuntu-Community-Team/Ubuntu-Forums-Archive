---
title: "BOOT Manager and more OS Installs???"
date: 2008-03-17
forum: General Help
---

### Post by badspell68 on 2008-03-17
Using Ubuntu , the newest one

I New to Linux and not all that technical!

I installed on a Dell PC using the whole HD and would like to now install a boot manage so I can install DOS, Win 98 and another Linux distro. How do I do this and would anyone have an easy step by step for doing so with recommended applications???

Thanks all!

---

### Post by Oldsoldier2003 on 2008-03-17
> **badspell68 said:**
> Using Ubuntu , the newest one

I New to Linux and not all that technical!

I installed on a Dell PC using the whole HD and would like to now install a boot manage so I can install DOS, Win 98 and another Linux distro. How do I do this and would anyone have an easy step by step for doing so with recommended applications???

Thanks all!

try installing a VM such as VirtualBox or VMWare and running the other OSes inside the virual machine. Makes it real easy to swap OSes and has the benefit of not screwing with your grub..

What I consder to be the absoulte best part of this idea is  that if you run windows in a VM and it gets full of virii  you just delete the VM image and reinstall, no worrying about cleaning up the mess...

---

### Post by badspell68 on 2008-03-17
Any of them free?

Thanks!

---

### Post by thinkdez on 2008-03-17
I would recommend the VM's as well as its easier to work with.  However should you want to do a Multi-Boot you should look into GRUB.  Its a boot loader that is installed with Ubuntu.  The only thing you will have to make sure of is that you have sufficient disk space to install your alternate OS of choice.  You can use PartImage to re-partition your disk but this could be tricky and you could lose data if your not careful.


As for Virtual Machines  Virtual Box is open source.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by bodhi.zazen on 2008-03-17
> **badspell68 said:**
> Using Ubuntu , the newest one

I New to Linux and not all that technical!

I installed on a Dell PC using the whole HD and would like to now install a boot manage so I can install DOS, Win 98 and another Linux distro. How do I do this and would anyone have an easy step by step for doing so with recommended applications???

Thanks all!

Virtualization is a great idea.

If you are wanting to "simply" multiboot, the boot manager in Ubuntu, and in most distros these days, is Grub.

Grub will boot almost anything :

[http://www.strangehorizons.com/2004/20040405/badger.shtml](http://www.strangehorizons.com/2004/20040405/badger.shtml)

:lolflag:

The problem, of course, is it is not always so user friendly.

Install windows first, then Linux ang GRUB should be, for the most part, automatically configured.

Here is the best grub manual I know of :

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Yappy on 2008-03-24
Hi... the trouble is after installing Ubuntu, I lost all my data on the disk.

I had 2 HDs. One 40g an the other 120. WinXp is on my 40g and Linux is on the 120g.

All my data are store in 120g...... and also I have another Linux on the 120g.. Slakeware.

How do I recover the data in the 120g HD?

---

