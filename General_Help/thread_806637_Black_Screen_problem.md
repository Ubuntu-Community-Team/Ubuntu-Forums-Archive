---
title: "Black Screen problem"
date: 2008-05-25
forum: General Help
---

### Post by In-flux on 2008-05-25
Hi,

I am having a problem when loading Linux where the system dies and the monitor goes blank. The monitor actually goes to standby which indicates there is no monitor feed from the system. When this happens the PC is still running, but it cannot be reset with the keyboard or turned off with any soft-off buttons.

I believe the problem is graphics related as the crashes occur whilst I am doing something graphical such as resizing a window, or rolling the mouse over a link. Crashes can occur on the splash welcome screen when scrolling over the options button, and always occurs when trying to login to GNOME. I am sometimes able to login under failsafe mode, but the system will always crash at some point. Again, always when doing something graphical.

I am a n00b in linux so am unable to provide any more details than that. I have attempted to update drivers, including installing the nvidia experimental drivers, but this did not help.

I would really appreciate some help with this as my PC is unusable in this state!!

---

### Post by graemelljn on 2008-05-25
I believe I'm having this problem as well, it has only started happening in the last couple weeks, prior to this it was stable and I have not changed anything. I think it's probably faulty hardware but since I'm not the only one having this problem I'm not sure now. I'm using an ATI card and the proprietry drivers, which may not be up to date.

---

### Post by In-flux on 2008-05-26
Ok, I am still having problems.

Have now uninstalled the restricted drivers and installed the drivers from the nvidia website. This has not helped. In fact it seems to be worse than before. 

Is there anyone out there that can point me to some information on how to fix this??

---

### Post by nbayiha on 2008-05-28
@ In-flux try to follow this thread maybe that will help you 
[http://ubuntuforums.org/showthread.php?t=765985&page=3](http://ubuntuforums.org/showthread.php?t=765985&page=3)

@ for the rest please give us more information about your system, i mean , you graphic card , which version of ubuntu are u trying to install, which kind of processor do u have. If we don't have those information it's a kind of hard for us to help you guys.

---

### Post by In-flux on 2008-05-28
Thanks nbayiha,

I have managed to recover my system to a workable state by using the generic drivers. I tried installing the nvidia drivers in a similar way that you described in your post, but I still had the same problem. I'll give your method a shot.

As for system details:
 - Ubuntu 8.04 AMDx64
 - NVidia GeForce-6600 256Mb (GV-NX66256DP)
 - AMD64 single core processor

---

### Post by nbayiha on 2008-05-29
When u install ubuntu 8.04 did u install **the alternate install cd** one ? 
I mean if u do a clean instalation of ur system with the alternate cd , you should have you problem fixed.
But i know before doing that you have to tried all possible method. 
First tell me if you have nvidia's driver installed ? If so tell me which one you have.
Open your synaptic and write nvidia and tell me which one is installed .

And by the way are u using a notebook ?
Do you use compiz-fusion ?

---

### Post by bpl07 on 2008-05-29
I have this problem too on a dell inspiron 1501 running ubuntu 8.04, AMD64, generic kernel 2.6.24-17, with integrated ati xpress 1150 graphics.  I use the proprietary drivers installed by EnvyNG.  I actually have [another thread]("http://ubuntuforums.org/showthread.php?t=810064") where I described trying to fix various errors in my dmesg, primarily the iommu aperture one.  It apparently didn't work because the crash happened again this morning.

---

### Post by nbayiha on 2008-05-29
@bpl07 did u try this [http://ubuntuforums.org/showthread.php?t=765985&page=3](http://ubuntuforums.org/showthread.php?t=765985&page=3) , if not tried it first and tell me what u got.

---

### Post by In-flux on 2008-05-29
nbayiha,

I did not install this version from the alternate CD. I have only recently converted to Linux and went with the easiest install.

I had the nvidia driver installed, but this was causing me the problems. I had this driver (NVIDIA-Linux-x86_64-173.14.05-pkg2.run) which i got from this site. ([http://www.nvidia.com/object/linux_display_amd64_173.14.05.html]("http://www.nvidia.com/object/linux_display_amd64_173.14.05.html"))

I am running on a desktop, not a notebook. I currently have the generic drivers installed and am not crashing. I am not sure what compiz-fusion is, but will check my system tonight and install it if not present.

---

