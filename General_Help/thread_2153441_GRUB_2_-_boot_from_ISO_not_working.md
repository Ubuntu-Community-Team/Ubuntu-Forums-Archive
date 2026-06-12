---
title: "GRUB 2 - boot from ISO not working"
date: 2013-06-11
forum: General Help
---

### Post by gigenieks on 2013-06-11
Hello!

First, I detected that Ubuntu randomly change HDD order:
[IMG]http://i59.photobucket.com/albums/g295/gigenieks/Multi%20Live%20CD%20USB/80and120GBchangesplacesrandomly_zps9bf2a756.png~original[/IMG]
As far as I know it doesn't happen often, but it does happen. I noticed that 80GB hard drive is either first (sda) or third (sdc). 
Note 1: 80 GB is SATA, rest are IDE drives.
Note 2: SATA disk contains Win8. 120 GB IDE disk contains Ubuntu.
Not sure if the info above is relevant.

Second, I'm trying to add menuentry for ubuntu-13.04-desktop-i386.iso, but have failed.
Here is my /etc/grub.d/40_custom file:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry “ISO Ubuntu” {
set isofile=”/home/juris/Downloads/ubuntu-13.04-desktop-i386.iso”
loopback loop (hd1,6)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nopromt noeject
initrd (loop)/casper/initrd.lz
}

```
It doesn't work at all. I don't even get menu (ISO Ubuntu) in GRUB2...

What's wrong?

Update: [post about IDE+SATA setup issue]("http://ubuntuforums.org/showthread.php?t=1549847&page=14&p=10822879#post10822879"), not sure if this applies to me:
[LIST]
[*]I don't get any menu added to my GRUB2 configuration
[*]When I restart and HDD order doesn't change it still doesn't show menu (therefore I can't boot from ISO)
[/LIST]

---

### Post by sudodus on 2013-06-11
> ... I'm trying to add menuentry for ubuntu-13.04-desktop-i386.iso, but have failed.
Here is my /etc/grub.d/40_custom file:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry &#8220;ISO Ubuntu&#8221; {
set isofile=&#8221;/home/juris/Downloads/ubuntu-13.04-desktop-i386.iso&#8221;
loopback loop (hd1,6)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nopromt noeject
initrd (loop)/casper/initrd.lz
}

```
It doesn't work at all. I don't even get menu (ISO Ubuntu) in GRUB2...

What's wrong?

Update: [post about IDE+SATA setup issue]("http://ubuntuforums.org/showthread.php?t=1549847&page=14&p=10822879#post10822879"), not sure if this applies to me:
[LIST]
[*]I don't get any menu added to my GRUB2 configuration 
[*]When I restart and HDD order doesn't change it still doesn't show menu (therefore I can't boot from ISO) 
[/LIST]


Try with this one, I have changed your double quotes to the standard ones (Ascii 34)

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "ISO Ubuntu" {
set isofile="/home/juris/Downloads/ubuntu-13.04-desktop-i386.iso"
loopback loop (hd1,6)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nopromt noeject
initrd (loop)/casper/initrd.lz
}

```

---

### Post by Cheesemill on 2013-06-11
Also remember you need to run...
```
sudo update-grub
```
every time you have edited any of the grub configuration files before the changes will take effect.

---

### Post by oldfred on 2013-06-11
If the drive you boot from BIOS or one time boot key is the drive with grub then it should be hd0. I have multiple drives, only SATA and they normally are in SATA port order for sda, sdb. But in grub the boot drive is always hd0. Sometimes you need to use e in grub menu and manually edit entry or a quick way to test alternatives.

BIOS with IDE & SATA drives often seem to mount drives in different orders. It just may be which one comes up to speed first.

---

### Post by grahammechanical on 2013-06-11
The sda designations also depend on which Sata port the drive is connected to. The Sata ports are numbered. Also, if you disconnect the drive connected to Sata port 1 and leave the drive plugged into Sata port 2 still connected then what was once sdb now becomes sda until you plugged the drive back into Sata port 1 again.

The really important thing to keep in mind is the fact that Ubuntu uses a UUID for each partition in the Grub Configuration files. The UUID does not usually change. So, by booting to a UUID Grub will still load the OS that we select.

>     linux /boot/vmlinuz-3.2.0-40-generic root=UUID=384ce6c1-d479-432c-acb1-1ce3823a60b3 ro quiet splash $vt_handoff


This is for Grub itself

>     set root='hd0,msdos1'

Means first hard disk and first partition but once grub is looking there it searches for and loads vmlinuz-3.2.0-42-generic file, which is the Linux kernel and that uses the UUID to set root. Which has not been changed. whereas the sda designation may have changed. Clever stuff. Yes?

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

Regards.

---

### Post by gigenieks on 2013-06-11
OK, guys finally it works. I can launch Ubuntu, Kubuntu and Xubuntu from grub menu. Here is my /etc/grub.d/40_custom contents:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "ISO Ubuntu" {
set isofile="/home/juris/Downloads/ubuntu-13.04-desktop-i386.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nopromt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "ISO Kubuntu" {
set isofile="/home/juris/Downloads/kubuntu-13.04-desktop-i386.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nopromt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "ISO Xubuntu" {
set isofile="/home/juris/Downloads/xubuntu-13.04-desktop-i386.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nopromt noeject
initrd (loop)/casper/initrd.lz
}

```
What was preventing previously them booting?
[LIST=1]
[*][IMG]http://i59.photobucket.com/albums/g295/gigenieks/Multi%20Live%20CD%20USB/solution_zps9ec185ba.png~original[/IMG]
Red arrows point on incorrect **_quotes_**. Just as sudodus said "change double quotes to the standard ones (Ascii 34)" 
(Note: I have NO idea what are double quotes etc)
[*]changd loopback line (from loopback loop [COLOR="#B22222"](hd1,6)[/COLOR]$isofile to [COLOR="#006400"]loopback loop $isofile[/COLOR] [removed red]
[/LIST]

[As you can see]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685732#post12685732") I had incorrect quotes and unnecessary (hdXY), both things prevented me from success. But I'm still confused why I don't need to use **(hdXY)** at loopback loop?? 
[In GRUB2/ISOBoot documentation]("https://help.ubuntu.com/community/Grub2/ISOBoot#Menuentry_Details") they say (hdXY) is necessary. There are no examples where they didn't use that (hdXY)... Can someone explain this to me?!

---

### Post by oldfred on 2013-06-11
When directly booting a flash drive I do not have the (hd0,1) setting. But when booting from a hard drive that may be different than default boot drive I include the device setting for grub.
I also boot from a gpt drive so I also have to add insmod settings as it includes a default for msdos partitioning. If not using FAT32 I also include insmod for NTFS or ext2 just to be sure it has the correct driver for my format. 

I think if it is the same drive it uses that and it does not have to be specified. Anything else must be specified.

I boot sdd as default and have ISO in my sdb drive which is gpt partitioned. So this is my entry for that:

> menuentry "Ubuntu 13.10 Saucy ISO 64bit" {
    set isofile="/iso/saucy-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}


But from my flash drive this is my entry:

> menuentry &#8220;Ubuntu 13.04&#8221; {
set isofile=&#8221;/ubuntu-13.04-desktop-amd64.iso&#8221;
loopback loop $isofile
inux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}


---

