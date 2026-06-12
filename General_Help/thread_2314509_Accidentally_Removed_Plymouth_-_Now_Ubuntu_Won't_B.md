---
title: "Accidentally Removed Plymouth - Now Ubuntu Won't Boot"
date: 2016-02-21
forum: General Help
---

### Post by hog2 on 2016-02-21
Hey guys, I have been an Ubuntu-user for years now, and this is my first time posting, so please go easy on me. 

I have a crisis on my hands. I have an MSI GS60 that's been dual-booted with Ubuntu 14.04 since I got it about a year ago. It's been running alongside Windows 8 up until a couple of weeks ago when I updated to 10 (no issues). I dominantly use Ubuntu and rarely use Windows, as I do a lot of statistical, programming, and visualization work for school. (And I despise the limited-abilities of Windows.) 

I had some issues last week with my resolution and graphics that (I thought) were resolved. After tweaking with the settings and configurations, it was booting and shutting down with the gaudy-looking console text. After Googling, I came across the Plymouth Boot Manager, which ended up causing more harm than good. I went to uninstall it and instead of removing "plymouth boot manager", I uninstalled "plymouth". That completely rendered my Ubuntu unusable. After that my Ubuntu partition has been unable to boot at all. 

When I boot, it still loads Grub, because my default Grub boot loader screen is still there with all of my boot options, and all of the previous kernels available. I am able to get to the Grub command line and edit the current grub settings using the "c" and "e", respectively. When I am able to 'boot' into any of the Ubuntu kernels, it goes through the console text, and the last main section says "Target file system doesn't have requested /sbin/init." and stops at that section, remaining stopped until I turn it off. I have tried changing the BIOS options to every possible combination possible: switching between UEFI, Legacy, and UEFI and CSM (I think it's called), turning on and off FastBoot, and turning on and off SafeBoot. 

I have tried booting the Boot Repair from a live USB, as well as the Ubuntu installation from a live USB, and they both load directly into the Grub CLI. Upon exit of that, it brings me right to the standard Grub list where I choose between Ubuntu or Windows, and the process starts all over again. 

I have also tried starting the plain text CLI by hitting ctrl+alt+F1 at all the stages at startup, but that doesn't do anything.

Thankfully I still have full usable access to my windows partition. I was wondering if anyone had any solutions? It would be fantastic if someone had any ideas on how to restore the ability to just get to a recovery-mode so that I could reinstall plymouth. 
Or, if anyone had any idea as to whether cleaning off the Linux partition is an option and doing a clean reinstall. (Which wouldn't be the end of the world - all my data and files are located on an external hard drive just for reasons like this.)

Any suggestions at all would be help, and if you need any information, please tell me and I will do my best.

---

### Post by ian-weisser on 2016-02-21
No 'recovery mode' will help.
Lack of /sbin/init due to a mere grub hiccup can be repaired. Init still exists, it's just hidden.
Lack of /sbin/init due to package (and dependency) removal is irecoverably fatal - the beating heart of your system has been cut out and thrown away. This seems to be your problem.

I think you have two options:
1) You can boot a LiveUSB, chroot into your broken system, and reinstall ubuntu-standard (including Plymouth)
2) You can reinstall.

---

### Post by hog2 on 2016-02-21
Do you know how I could manage to get it to read the live USB? When I try to do so, it brings me directly to the Grub CLI. Is there a way to access the system through that to tell it to boot to it?

---

### Post by ian-weisser on 2016-02-21
> **hog2 said:**
> Do you know how I could manage to get it to read the live USB? When I try to do so, it brings me directly to the Grub CLI. Is there a way to access the system through that to tell it to boot to it?

Yes, that's Option #1.

Your hard drive uses GRUB. Your LiveUSB uses 'syslinux' instead of GRUB. If you are seeing GRUB, then you are trying to boot from the hard drive.

You must boot from the LiveUSB,  not the hard drive. You probably did this long ago when you first  installed. Do you recall how you did it back then?

---

### Post by hog2 on 2016-02-22
I do now. I was unable to load the live USB because I now realized I had formatted it wrong - Windows automatically formatted it with NTFS, but when I overrode it with 'FAT32 quick' it worked. 

I ended up having to fix Grub with the Boot Repair (twice), and completely reformat the partition that Ubuntu was on and reinstall it. I have Ubuntu up and running and working better than ever. 

Thank you for your assistance!

---

