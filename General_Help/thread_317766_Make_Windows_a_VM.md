---
title: "Make Windows a VM"
date: 2006-12-12
forum: General Help
---

### Post by Megaqwerty on 2006-12-12
I was wondering how I would make my Windows installation available for me to use from inside Ubuntu. I know that there is a software out there called "VMWARE" and that this program may help me. However, I wish to be able to access my Windows partition without damaging or changing anything in it. I want to be able to boot into it, or access it directly from Ubuntu. 

Is this possible?

For that matter, is any of this possible?

Thanks,

Megaqwerty

---

### Post by yer on 2006-12-12
You can mount your windows drive and read the files, if that is what you mean.

---

### Post by Megaqwerty on 2006-12-12
> **yer said:**
> You can mount your windows drive and read the files, if that is what you mean.

No it isn't I wish to be in the windows GUI.

EDIT: Like the results of having a Windows XP VM

---

### Post by yabbadabbadont on 2006-12-13
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server)

Just follow those instructions to get the free vmware server software installed and running, then you can install any OS that vmware supports.  (all DOS and Windows versions are supported)

---

### Post by Megaqwerty on 2006-12-13
> **yabbadabbadont said:**
> [http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server)

Just follow those instructions to get the free vmware server software installed and running, then you can install any OS that vmware supports.  (all DOS and Windows versions are supported)

This looks like a great tutorial, however, it doesn't look like it will keep my current windows installation intact. :( 

Am I incorrect?

---

### Post by yabbadabbadont on 2006-12-13
Running an instance of windows that is installed to the hard drive, instead of inside of vmware, is a non-trivial task as it requires creating a different hardware profile in windows that matches the emulated hardware when run under vmware.  If you have windows already installed, then your best option may be to just dual boot between it and Ubuntu.  This is especially true if you plan on playing games while in Windows as vmware doesn't support 3D and DirectX/OpenGL.  (there are experimental options, but they don't support them)  If you aren't going to be playing games, and you have plenty of disk space, you could go ahead and install a copy of windows inside of vmware to see if it meets your needs.  If so, you could eventually remove the windows install from your hard drive.  You just need to see what works best for you and your needs.

---

### Post by houstonbofh on 2006-12-13
The short answer is that your real hardware and the emulated hardware are different bits.  Half the time Windows chokes if you change a motherboard.  You are changing the entire system.

---

### Post by Megaqwerty on 2006-12-13
> **houstonbofh said:**
> The short answer is that your real hardware and the emulated hardware are different bits.  Half the time Windows chokes if you change a motherboard.  You are changing the entire system.

Okay, thanks to you both, I think I'll stick with waiting for the reboot into windows when I need it ;) thanks though!

-Megaqwerty

---

### Post by igknighted on 2006-12-13
You can't run the programs, but you can mount the disk in Ubuntu and get to your files when you need them.

---

### Post by Megaqwerty on 2006-12-13
> **igknighted said:**
> You can't run the programs, but you can mount the disk in Ubuntu and get to your files when you need them.

If you look above, "Yer" said the same thing

---

### Post by igknighted on 2006-12-13
Ah, apologies.

---

