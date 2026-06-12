---
title: "Multiple distro: grub rewritten"
date: 2007-08-18
forum: General Help
---

### Post by clinto on 2007-08-18
Okay, I'm going to try to keep this brief. Had one hd with Windows. Bought a second and partitioned it to hold 3 distros. Installed Debian on one, then Ubuntu on the second. Grub doesn't include Debian now. Figured I could just add Debian's vmlinuz and initrd to the menu.lst but when I used cd to move to the partition with Debian, nothing was in /boot.

How do I get grub to include Debian now? I'm stumped... and very tired. :(

---

### Post by BoneKracker on 2007-08-18
Somebody's more likely to be able to help you with this one if you post your menu.lst file.

I'm speaking from memory and haven't used Ubuntu in a while, but I'll try to help.  What I'm telling you might be outdated or even just plain wrong.  Also, I'm going to explain this in a very wordy fashion, because it has been my experience that people are very confused by bootloaders -- so please don't be offended if you know all this and it wasn't necessary.

Ubuntu used to have a script (called "update-grub") to help you update your GRUB configuration file following a kernel update or similar activity.  This script (a Debian option) used to be active by default and probably still is.  It's no problem to dual/multi-boot Ubuntu with other instances of GNU/Linux (whether they be Ubuntu or other distributions);  just ensure that in your menu.lst file, you place the kernel image section for other instance(s) ***outside*** the portion of the text that is automatically edited by the update-grub script.  That portion is clearly marked.

Now, if one of your other instance also assumes itself to be master and commander of the bootloader, then you will need to ensure that only one of them is able to make automatic changes such as mentioned above.  

For example, let's assume you decide to manage grub from within Ubuntu.  If so, you probably should avoid installing any bootloader at all as part of your other GNU/Linux instances.  While it's not strictly necessary, this is to avoid version mismatches and having each distro over-write the other one's information in the mbr (which may be exactly what happened in your case).  Also, you may want to install Ubuntu first, so you can use the bootloader as needed during the other installation processes.

If you do this, every time you update your kernel in one of the other (non-ubuntu, in this example) instances, you will need to manually edit GRUB's menu.lst file.  So you may want to have a separate /boot partition in Ubuntu so you can access it from the other instances without mounting the root filesystem.
[Edit]: Or (easier), in the other (non-ubuntu) instances, inside the boot partition/directory create a soft link to the kernel image and give it a name that will not change (like 'kernel' or something).  Then, in your menu.lst file, you can specify the name of the symlink instead of the full name of the kernel image file.  Same goes for initrd files if you use them.  That way, you never have to modify the menu.lst file, you just re-create the symlink when the filename changes.

---

### Post by clinto on 2007-08-18
BoneKracker, that was VERY helpful. Thank you so much.

Now that I'm rested, I've realized what I've done. I had made a separate boot partition for Debian, but when I installed Ubuntu, I must have selected the same partition for *it's* boot. I can't believe I did that.

This is what I get:
```

clinton@koenigdesk:/home/hdb7$ ls
bin    dev   initrd      lost+found  opt   sbin     sys  var
boot   etc   initrd.img  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib         mnt         root  srv      usr
clinton@koenigdesk:/home/hdb7$ ls boot/


```

Your post has called another thing to my attention. I've edited my menu.lst taking out all the commented lines. I'm thinking that needs to be kept in place in order for grub to be updated, no?

```

default		0
color cyan/blue blink-white/blue


title		Ubuntu Feisty(hdb6)
root		(hd1,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=097f966e-f64a-447e-bb49-da7d0124a02b ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
boot

title		Microsoft Windows XP Home Edition(hda1)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		*-----------------------------------*
root

title		Debian GNU/Linux, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=097f966e-f64a-447e-bb49-da7d0124a02b ro single
initrd		/initrd.img-2.6.20-16-generic
boot

#title		Debian GNU/Linux, kernel 2.6.20-15-generic
#root		(hd1,0)
#kernel		/vmlinuz-2.6.20-15-generic root=UUID=097f966e-f64a-447e-bb49-da7d0124a02b ro quiet splash
#initrd		/initrd.img-2.6.20-15-generic
#boot

#title		Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
#root		(hd1,0)
#kernel		/vmlinuz-2.6.20-15-generic root=UUID=097f966e-f64a-447e-bb49-da7d0124a02b ro single
#initrd		/initrd.img-2.6.20-15-generic
#boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd1,0)
kernel		/memtest86+.bin 
boot

```

I think I'm just going to install a different distro anyways. Ubuntu is based on Debian and is very similar. Since other family members are going to be using this pc, I'll leave Ubuntu and then install a couple others just to dabble in. I definitely want to get Gentoo on here. I may try Slackware or Fedora as well. I probably should learn how to fix Debian though. I'm sure there's a way to do it without reinstalling it.

PS: It's nice to see those who use Gentoo around here. ;)

---

### Post by BoneKracker on 2007-08-19
Glad it helped.

Yes, I believe the update-grub script reads the text to identify the section containing its configuration parameters and the kernel images, and if I recall correctly, the boundary-markings it uses may in fact have been comments.

You could trash the update-grub script.  I don't know where within the package management system it gets called, but it should be a simple matter of commenting a line in some script that gets run after new packages are installed.  Another way that would probably work would be ditch GRUB and use LILO.  LILO's not as fancy with the menu, but it has been modernized and isn't really as "old school" as people think.  I'm assuming, maybe incorrectly, that there is not some OTHER script like update-grub that would then magically appear.

Ubuntu is a wonderful distro.  They've done a really good job putting together a Debian system that meets most needs and takes advantage of many performance-enhancing options.  If you feel a desire to tinker, learn, customize, etc., a good place to start would be with Debian.  You were headed down that path, and I think it's a good idea.  That way, you can leave Ubuntu in place and refer back to it to see how they configured it, copy what you like and get rid of what's not useful to you.

Beyond that, there are lots of interesting things to try.  Some good learning experiences include:

- Try a Redhat-based distribution.  They do some things very differently than Debian and it's useful to understand what is "common ground" and what is different (and why).  Fedora, OpenSUSE, Centos, are good choices.
- Try a BSD.  BSD is closer to being a true UNIX and thus provides historical context as well as revealing some things about Linux that are somewhat questionable.  FreeBSD is popular and a good choice if you want to build a desktop system, but I recommend trying OpenBSD first because it's tightly put together and provides a better learning experience (it's also great if you want to build a firewall/router).
- I haven't tried Slackware, but from what I have read this would also be a good choice for gaining a solid grounding in GNU/Linux.
- Gentoo requires you to get your hands very dirty, and therefore offers a good learning experience.  It is also a good choice if you want a system that is highly optimized for your hardware and your uses.
- If you happen to have an AMD64, you can try Solaris.  Like BSD it's closer to being real UNIX.  I didn't keep it installed long, though, because it seemed you had to pay if you wanted full access to the updates repository.

Good luck and have fun!

---

### Post by clinto on 2007-10-09
Well, I have a new problem now. :D

I had Ubuntu installed on one partition and decided to set up openSUSE 10.2 on another one. I let it create it's own Grub and figured I could just edit Ubuntu in later.

Apparently, openSUSE installs Grub a little differently than Ubuntu does. For example, I'll put both menu.lst files up. First the one from Ubuntu:

```

abnerdoon@koenigdesk:/boot/grub$ cat menu.lst

default         0
color cyan/blue blink-white/blue



### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdb6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

#title          Debian GNU/Linux, kernel 2.6.20-16-generic
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro 
#initrd         /initrd.img-2.6.20-16-generic
#boot

#title          Debian GNU/Linux, kernel 2.6.20-16-generic (recovery mode)
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro single
#initrd         /initrd.img-2.6.20-16-generic
#boot

#title          Debian GNU/Linux, kernel 2.6.20-15-generic
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-15-generic root=/dev/hdb6 ro 
#initrd         /initrd.img-2.6.20-15-generic
#boot

#title          Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
#root           (hd1,0)
#kernel         /vmlinuz-2.6.20-15-generic root=/dev/hdb6 ro single
#initrd         /initrd.img-2.6.20-15-generic
#boot

#title          Debian GNU/Linux, kernel memtest86+
#root           (hd1,0)
#kernel         /memtest86+.bin 
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP Home Edition on hda1
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu Feisty(kernel 2.6.20-16-generic) on hdb6
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro 
initrd          /initrd.img-2.6.20-16-generic
boot

title           Ubuntu Feisty(recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/hdb6 ro single
initrd          /initrd.img-2.6.20-16-generic
boot

title           memtest86+
root            (hd1,0)
kernel          /memtest86+.bin 
boot

```

Now the one from openSUSE:

```

abnerdoon@koenigdesk:/home/hdb7/boot/grub$ sudo cat menu.lst
# Modified by YaST2. Last modification on Tue Oct  9 18:50:58 EDT 2007
default 0
timeout 8
gfxmenu (hd1,6)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.2
    root (hd1,6)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/hdb7 vga=0x31a resume=/dev/hdb2 splash=silent showopts
    initrd /boot/initrd-2.6.18.2-34-default

title Ubuntu 7.04
    kernel (hd1,0)/vmlinuz-2.6.20-16-generic root=/dev/hdb6 vga=0x31a resume=/dev/hdb2
    initrd (hd1,0)/initrd.img-2.6.20-16-generic

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (hd0,0)
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.2
    root (hd1,6)
    kernel /boot/vmlinuz-2.6.18.2-34-default root=/dev/hdb7 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.18.2-34-default


```

NOTICE! I have the /boot for Ubuntu on the first partition of the second hard drive. Yeah, my crap is a mess and I should probably just start all over again. :/

The Ubuntu 7.04 section is what I added. With this, I was able to boot into Ubuntu from the boot loader. However, I get a filesystem error while it tries to boot into it's partition. Does anyone know why this might be? I'm sure it has something to do with the way grub is set up differently. I'm just not sure what exactly the problem is. Thanks.

---

