---
title: "Uninstall Ubuntu, Install Kubuntu (and preserve Windows XP)"
date: 2007-11-15
forum: General Help
---

### Post by toasty2 on 2007-11-15
How can I uninstall Ubuntu (or safely delete it or whatever) and then install Kubuntu. I'd like to preserve my Windows install as well. If I delete Ubuntu will there be GRUB problems? How do I go about this? Also, how do I change the default OS to boot?

---

### Post by CptPicard on 2007-11-15
AFAIK you just need to install "kubuntu-desktop" and you're set. Kubuntu and Ubuntu are otherwise identical under the hood...

---

### Post by toasty2 on 2007-11-15
I am aware I can do that, but I want to remove Ubuntu and install from scratch (Kubuntu or possibly another distro).

---

### Post by sipickles on 2007-11-15
Any help?

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Or for a clean install, just boot from a Kubuntu boot disk, and reformat your ubuntu partitions using the live CD disc partitioner (as part of the install process). Your windows will be fine.

I have done this a few times (although it was gnome over gnome)

hth

---

### Post by erginemr on 2007-11-15
That is an easy task. First, you should salvage anything of importance to you, from your existing Linux hard disk (such as your documents, music files, etc.), to either a CD-R, pen drive or to your Windows drive(s).

Second, you will boot up with the Kubuntu Live CD, let the installlation begin, and when it comes to the partitioning phase, you should select "manual partition", select "/" (for root drive) for the existing Ubuntu hard disk, select its check box to re-format it with "ext3", select your existing "swap" drive (used by linux for swap memory) for swap again (or leave it that way, the installer will automatically detect it and use it for swap), and proceed with the installation of Kubuntu from thereon.

Don't worry about Grub; Kubuntu will reinstall Grub into the master boot record (MBR) with correct boot menu settings as recorded in the file: /boot/grub/menu.lst

Good Luck.

---

### Post by erginemr on 2007-11-15
To your second question (default OS to boot), it is handled inside the file:
/boot/grub/menu.lst

This file stores a bunch of settings, which you can use to customize your Grub menu. It is really organized in a simple and orderly manner. If you read it through, you will get the hang of it very soon.

In there, there are two lines of interest:
default 0 #The entry which should be booted by default
timeout 5 #The number of seconds GRUB should wait before booting an OS 

The first item is the default item to activate (i.e. the one you are looking for), starting from zero. To the end of the file, you will see uncommented (without # signs) hard disk selection groups including the one for Windows. You should count from zero up to find the correct system to specify as default.

Timeout is simply the amount of time in seconds after which the default OS selection will be activated and will start, if no one touches the keyboard. For instance, in a file like;
.....
default 1
timeout 5 
.....
title Red Hat Linux
root (hd0,4)
kernel /boot/vmlinuz-2.4.18-14 ro root=/dev/hda5
initrd /boot/initrd-2.4.18-14.img

title Debian
root (hd0,6)
kernel /boot/vmlinuz-2.2.20-idepci ro root=/dev/hda7

title WinXP
rootnoverify (hd0,0)
chainloader +1 
......
the default operating system to load is Debian and the wait-out time is 5 seconds.

For a thorough tutorial on Grub menu settings, please refer to:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by namanbagga on 2007-11-15
You won't have problems with Grub as it will detect other operating systems.So go ahead,format your Ubuntu partition after preserving your useful information by storing it elsewhere.If you have any problems with grub(which you won't),try [:this]("http://www.namanb.com/2007/11/when-computers-dont-boot.html"). :popcorn:

---

### Post by toasty2 on 2007-11-15
I've got another question. What if I want to remove GRUB and go back to just Windows (and use its bootloader, not GRUB)? The reason I would want to do this is because I will be installing another Windows version (specifically, Windows Server 2008 Beta) for testing purposes. Then I may add Linux later. Any recommendations to go about doing this?

---

### Post by erginemr on 2007-11-16
Then you have to remove the Ubuntu / Linux partitions first. And after you make sure that you can use those partitions under Windows, you should use Windows Setup CD to boot into the recovery console and use the command "fixmbr" to eradicate the grub bootloader from the mbr (master boot record) and restore the one for Windows.

---

### Post by erginemr on 2007-11-16
Also please refer to the following thread:
[http://ubuntuforums.org/showthread.php?t=597713](http://ubuntuforums.org/showthread.php?t=597713)

There I have done my best to explain the procedure.

---

### Post by namanbagga on 2007-11-16
Format the Linux Partitions and run FIXMBR from the Windows XP CD.It's explained in the first part of [this]("http://www.namanb.com/2007/11/when-computers-dont-boot.html") post.:):)

---

### Post by toasty2 on 2007-11-16
Well, since its about time for my routine Windows reinstall, I'll just do it instead. Is it safe to just delete all partitions and start over? (but I'll be leaving one of my file partitions) I assume GRUB isn't anywhere on that partition so it should be ok.

---

### Post by toasty2 on 2007-11-17
Does GRUB have any problems with Windows Server 2008? (it's similar to Vista)

I'd like to install Kubuntu now, I have Windows XP and Windows Server 2008 RC0 installed (using the bootloader of the latter).

---

