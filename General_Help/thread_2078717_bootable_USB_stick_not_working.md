---
title: "bootable USB stick not working"
date: 2012-10-31
forum: General Help
---

### Post by sovre on 2012-10-31
I have a Samsung laptop (new, purchased this year) wth a Windows 7 installation on which I tried to do an in place upgrade. The upgrade failed, the rollback failed, and now I can't gain access to the desktop. 

Since I don't have any discs on hand right now, I would like to use a USB stick with a Ubuntu installation to gain access to the files on my hard drive but it is not working for me.

I used Ubuntu 12.10 and pen drive linux to create the bootable USB stick. Pen drive linux said the process completed successfully.

My BIOS has an option for "USB hard drive" to which I have given priority.

However, when I boot the USB stick is not recognized at all. No Ubuntu installation appears in my boot options. I just have the two options I had before "Windows 7" and "Windows Setup Rollback" (the second being useless, because it won't rollback).

I don't know if something relating to the failed upgrade is preventing my system from checking for other boot options or if there is some other explanation.

Any ideas why Ubuntu isn't being recognized? Would I maybe have better luck if I burned my 12.10 image to a disc and tried booting from that?

Thanks for your help.

---

### Post by dentaku65 on 2012-10-31
Hi,

the usb pen drive with Ubuntu works on another PC?

If no, try to build usb pen drive with Ubuntu inside Windows 7 with [Unetbootin]("http://unetbootin.sourceforge.net/"); of course using the windows version

by

---

### Post by Topsiho on 2012-10-31
> **sovre said:**
> 
I used Ubuntu 12.10 and pen drive linux to create the bootable USB stick. Pen drive linux said the process completed successfully.


You could try the tool that comes with Ubuntu, which in English probaby is called "Create bootable disk" or something like that. The disk in fact is, or can be, a USB stick, of at least 1 or 2 GB. I use this tool quite often, with great success, creating a persistent file on the stick too, to keep any updates and settings, and files.

If you use a stick that has been used, you can have it wiped (all contents will be lost, so back it up if you don't want to loose it), and should have some patience, until it lets you install the OS, and create a persistent file.

---

### Post by oldfred on 2012-10-31
My BIOS has many USB boot options and it took me forever to find out that my USB flash drive is really a choice under which hard drive to boot from. 

So with f12 on my system as the one time boot key, I choose hard drives and if flash drive is bootable it appears as a boot choice.

---

### Post by aisajib on 2012-10-31
> **Topsiho said:**
> You could try the tool that comes with Ubuntu, which in English probaby is called "Create bootable disk" or something like that. The disk in fact is, or can be, a USB stick, of at least 1 or 2 GB. I use this tool quite often, with great success, creating a persistent file on the stick too, to keep any updates and settings, and files.

If you use a stick that has been used, you can have it wiped (all contents will be lost, so back it up if you don't want to loose it), and should have some patience, until it lets you install the OS, and create a persistent file.


I'm having some issues since my Linux Mint doesn't have Startup Disk Creator anymore. Please see if you can give me a solution to this: [http://ubuntuforums.org/showthread.php?t=2078787](http://ubuntuforums.org/showthread.php?t=2078787)

---

### Post by Topsiho on 2012-11-01
I saw your post, but did not know what to answer.
I saw the same black screen once upon a time, but don't remember how I solved that problem.

You could try and use different boot options, such as noapic or so.

Probably you could boot in recovery mode and try the options you find there.

You could also google for suggestions to solve this.

Anyhow, I managed to solve this problem in some way, but am really sorry I don't rember how. Probably using the recovery mode :)

Topsiho

---

