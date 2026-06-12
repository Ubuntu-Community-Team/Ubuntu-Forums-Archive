---
title: "Windows Auto Boots instead of Ubuntu with GNOME?"
date: 2008-05-21
forum: General Help
---

### Post by OMNIslash3D on 2008-05-21
Hey, I currently have Ubuntu and Windows installed, and both install working separately with 2 partitions on the same disk. Is there any way I can get windows to be the program selected when it comes time to choose operating systems, so that I don't have to auto choose windows XP? I want XP to automatically boot since that is what I'm going to be using most of the time. Thanks

---

### Post by Exsecrabilus on 2008-05-21
I'm assuming you have your resposotories enabled.

In Terminal in Ubuntu, (if you can access it) type:

```
sudo apt-get install startup-manager
```

Now go **System** >> **Administration** >> **StartUp-Manager**.

Check on the box next to the text *Show bootloader menu*.

If you cannot access Ubuntu, here:
On start-up, there should be something along the lines of:
To access bootloader menu, press <key>

---

### Post by OMNIslash3D on 2008-05-21
```
sudo apt-get install startup-manager
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startup-manager
```

:-(
Doesn't seem to work. I'll restart ubuntu looking for that boot loader menu, but I don't remember seeing it. I'll double check. Where can I get the startup-manager package if this doesn't work?

---

### Post by OMNIslash3D on 2008-05-21
Nope, I don't see the menu. I should have full access to everything.  I just installed ubuntu and had it working at the same time as windows as of this morning though. So I'm not super versed in it yet. I should have full access to everything though. Any more ideas?

---

### Post by cdtech on 2008-05-21
The correct install name is:
sudo apt-get install startupmanager

You should be set....

---

### Post by sailor2001 on 2008-05-21
gksudo gedit /boot/grub/menu.lst    Starting with your ubuntu kernel as 0 count down to your windows boot loader (maybe 3?) and make that your default near the top of the menu

---

### Post by cubeist on 2008-05-21
> **OMNIslash3D said:**
> Nope, I don't see the menu. I should have full access to everything.  I just installed ubuntu and had it working at the same time as windows as of this morning though. So I'm not super versed in it yet. I should have full access to everything though. Any more ideas?

You don't need the startup-manager, it is just a graphical interface for your grub menu.

First, create a backup of your grub menu
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Open menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

At the bottom of this file you will see your OS's.  To boot XP as the default, simply move it (copy and paste) to the top of the OS list.  While you are in this file you can also change how long before grub displays... this is called the *timeout* option.  You can alter this file but do not change the formatting of text or else you won't be able to boot at all!

---

### Post by cdtech on 2008-05-21
For new Ubuntu user's I like to keep it simple for them......

---

### Post by OMNIslash3D on 2008-05-21
Awesome, thanks cdtech. Got it working. Much appreciated.

Hey, what would be a good way to learn how to start working with linux? I don't even know how to install programs. For instance, I downloaded GCC 4.3 and I have no idea how to install. Is there a place I can learn these basic things?

---

### Post by cdtech on 2008-05-21
Yu welcome, come back and see us ya hear?

---

### Post by Exsecrabilus on 2008-05-21
> **cubeist said:**
> You don't need the startup-manager, it is just a graphical interface for your grub menu.

First, create a backup of your grub menu
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Open menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

At the bottom of this file you will see your OS's.  To boot XP as the default, simply move it (copy and paste) to the top of the OS list.  While you are in this file you can also change how long before grub displays... this is called the *timeout* option.  You can alter this file but do not change the formatting of text or else you won't be able to boot at all!
I'm suggesting StartUp-Manager because of its GUI interface and its easy configuration to new users.

---

