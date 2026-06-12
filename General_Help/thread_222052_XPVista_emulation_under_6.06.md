---
title: "XP/Vista emulation under 6.06?"
date: 2006-07-24
forum: General Help
---

### Post by ebeyer on 2006-07-24
I've been poking through this thread on running Win98 on Hoary:

[http://www.ubuntuforums.org/showthread.php?t=39513](http://www.ubuntuforums.org/showthread.php?t=39513)

Has anybody had experience running XP or the Vista beta on Dapper Drake?  What methods have you tried and what has your experienc been?

Thanks.

EB

---

### Post by tiger2357 on 2006-07-24
First of all: **Why** do you want to run Windows on Linux?

However, it should work, probably with vmware server ([http://www.vmware.com/products/server/)](http://www.vmware.com/products/server/)). Installing is no problem, you should have no vmware installed before, but if, you have to delete anything of it. Then you install the server, extract the tarball, then sudo ./vmware-install.pl and follow the instructions. You have the linux kernel source and the kernel headers and the kernel build tools installed because the installer will build kernel modules.

After installing you can use it: build a new virtual machine, select the guest system, put the Windows Install CD in your cd-rom drive and install Windows. Thats it.

---

### Post by JoWilly on 2006-07-24
Best is [vmware]("http://www.vmware.com").

---

### Post by ebeyer on 2006-07-24
> **JoWilly said:**
> Best is [vmware]("http://www.vmware.com").

Given that VMware is best, how does Qemu with KQemu stack up?  Have you used it?  It's supposed to be Free.

EB

---

### Post by Donnut on 2006-07-24
I have used vmware and it is pretty good.  It didn't work with the rez of my widscreen, and i have almost no experiance with directx or if it supports it, Install vmware tools though, it improves performance.  The beta server version is free under linux and there is a how-to at this site.  I don't have the link handy, but just search around and I am sure you can find it.

---

### Post by JoWilly on 2006-07-24
> **ebeyer said:**
> Given that VMware is best, how does Qemu with KQemu stack up?  Have you used it?  It's supposed to be Free.

EB

Vmware is optimized and fast. It has a nice and easy gui. It supports all the devices you will need (usb, etc...). If you want to run vista, I guess vmware is the way to go.

qemu of course also works. Not as easy to setup, and I don't know if it supports visa at the present time (anyone ?).

---

### Post by JoWilly on 2006-07-24
And vmware player is free (and in the repos). So you can create a virtual machine with the trial version of the full vmware and then use it as long as you want with the vmplayer.

---

### Post by tiger2357 on 2006-07-25
VMWare Server is not in beta, its in stable version available, and the best is: it's free to use, but not under GPL! You have to agree an EULA, and you have to register and you get a serial number, but its really free.
Try it!

---

### Post by Karma_Police on 2006-07-25
> **JoWilly said:**
> And vmware player is free (and in the repos). So you can create a virtual machine with the trial version of the full vmware and then use it as long as you want with the vmplayer.

you can try this online tool to create empty virtual machines: [http://www.easyvmx.com/](http://www.easyvmx.com/)

---

### Post by ebeyer on 2006-07-25
> **Karma_Police said:**
> you can try this online tool to create empty virtual machines: [http://www.easyvmx.com/](http://www.easyvmx.com/)

Have any of you any practical experience using the vmware/xp solution to do anything like voice dictation?  My ambition is to use this to do Dragon NS 9; containing Windoze in a sandbox - at least until there is a Free solution that is as good or almost as good.

Thanks again for your thoughts.

EB

---

