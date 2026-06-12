---
title: "Stupid Question"
date: 2007-11-24
forum: General Help
---

### Post by torgrot on 2007-11-24
I have been using apci=force and/or pci=biosirqon the kernel in gutsy for a while.  I do notice that the load on the CPU is considerably less with apci=force as opposed to pci=biosirq.  If I don't use one of these when I select Ubuntu to boot from grub then I get trapped in an eternal reboot situation.  i.e. select Ubuntu hardware reboots almost immediately.  So my question is what do these switches do and should I care?:confused:

torgrot

---

### Post by scorp123 on 2007-11-24
[http://lxr.linux.no/source/Documentation/kernel-parameters.txt](http://lxr.linux.no/source/Documentation/kernel-parameters.txt)

---

### Post by torgrot on 2007-11-24
Yes, I used that document to solve my original problem, but I was shooting blindly.  I had some guidance but that was it.  How does it affect Ubuntu and/or should I care?

torgrot

---

### Post by scorp123 on 2007-11-25
> **torgrot said:**
>  How does it affect Ubuntu and/or should I care?  Highly depends on your hardware and how new or how old it is. 

For example: For "Feisty" (Ubuntu 7.04) I had to use the parameters "pci=bios acpi_sleep=s3_bios" on my HP laptop (hp dv2108ea) or else it would not suspend / hibernate + resume correctly. Now I upgraded that laptop to "Gutsy" and it works tip top without those parameters. I suppose something in the new kernel changed? I count that as an improvement, because now I can just forget about above parameters and count on it that any modern distro will just do its stuff right without having me to Google up any special parameters. That's good. 

On another laptop (Fujitsu-Siemens Lifebook C1410 ... IMHO a crappy laptop, sorry to say so) which is still running "Feisty" I have to use "pci=usepirqmask" or else the laptop will behave very very strange, will not see some of its internal devices, and suspend / hibernate + resume will not work at all and instead just badly corrupt the filesystem. With that parameter however it works tip top. 

So should you care? Hard to say. Really depends on a lot of factors.

I'd Google around if there are any "Linux installation success" reports for your particular PC model (or a similar one). Some hardware manufacturers don't always stick to given standards (such as ACPI!) and put some strange stuff into their product's BIOS'es which will then cause odd behaviour under Linux, and so sometimes you simply have to use such parameters or else Linux will never ever work on such a system.

The weirdest computer I ever had (and still have) was a Sony VAIO C1-VFK "PictureBook" sub-notebook which I bought back in 2002 .... If you wanted to run a Linux distro on it back then you had to use an extremely long list of kernel parameters or else this thing wouldn't even boot properly and get stuck half-way in the boot process. I just recently tested a fairly modern distro on it and I got all the hardware (even the proprietary Sony interrupt controller in there ... "sonypi") working without using any special boot parameter.

I'd therefore say that time too is a factor here. The more time passes and the better the Linux kernel gets, your chance of Linux being able to correctly deal with your hardware "just like that" and "out of the box" gets better and better.

What I really wonder is how old is your system? Usually you shouldn't have to use "acpi=force" on any fairly modern post-2000 system ....

---

