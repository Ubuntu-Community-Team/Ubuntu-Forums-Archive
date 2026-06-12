---
title: "Backup GRUB configuration?"
date: 2012-12-22
forum: General Help
---

### Post by GameX2 on 2012-12-22
Hi,


Is there an easy way to fully backup my GRUB configuration?
I've been reinstalling Ubuntu 12.04, since my Ubuntu was getting slower, with strange bugs I don't have the level to fix.  Reinstalling Ubuntu is a breeze, because all my software can be installed in one Batch script. :cool:

The problem with that is that I keep loosing my GRUB configuration.  It quite annoying, since I've allowed GRUB to boot from multiple Live-ISO files, and that I loose all these settings..  It's very long to set them back.
I would like to do a backup of my GRUB settings, so I don't have to reconfigure anything again.

I've tried backing up the grub.d folder, (Keeping the original folder somewhere else, of course) but that's not the way to go.

Can you help?

Thanks! :)

---

### Post by oldfred on 2012-12-22
What are you customizing with grub?

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.


I normally edit (and backup) 40_custom which is in /etc/grub.d, but if editing settings you may want to back up /etc/default/grub? The grub.cfg is rebuilt using the setting from /etc/grub and the scripts & custom entries in grub.d.

---

### Post by GameX2 on 2012-12-22
Yes, I'm talking mostly about custom entries;
What's annoying is that when my GRUB is erased and that I restore it, I have to change the name of the entries everytime, change the order of them, and all that.

The worst is also adding custom entries, to boot from an ISO.  I also loose these entries, and it's difficult for me to add them again.  I copy the file 40_custom that I have backed up to /etc/grub.d, but the entry won't appear in the menu - even after I type "sudo update-grub" in the Terminal.

Can you tell me what's wrong with my 40_custom file, please - Let's say I want to boot Lubuntu ?

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Lubuntu 12.04 : Precise Pangolin x86 [Live]" {
    insmod loopback
    insmod iso9660
    set isofile="/home/gamex/LUBUNTU1204X86.iso"
    loopback loop (hd0,6)$isofile
    echo    'Chargement du noyau Linux ...'
    linux (loop)/casper/vmlinuz locale=fr_FR bootkbd=fr console-setup/layoutcode=fr iso-scan/filename=$isofile boot=casper file=/cdrom/preseed/lubuntu.seed noprompt quiet splash --
    echo    'Chargement du disque mémoire initial ...'
    initrd (loop)/casper/initrd.lz
}

```I am confused with the line "  loopback loop (hd0,6)$isofile ".  How can I tell which partition # is correct?  Currently, the ISO is located in " /home/gamex/", on the partition SDA11 on the GParted screenshot (I have only one hard disk).

[http://img824.imageshack.us/img824/4706/capturedu20121222171227.png](http://img824.imageshack.us/img824/4706/capturedu20121222171227.png)

Thank you!

---

### Post by oldfred on 2012-12-22
From grub /home/gamex does not exist as that is mounted by Ubuntu later, unless gamex is your user id and the ISO is at the top level in your home. 
I just find it easier to use directories that grub sees by default. So I use /boot/iso or mostly folders on other drives.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

    
I also have changed to using a config file, so I can edit all my ISOs without having to run sudo update-grub which I forget half the time.

So this is my entry in 40_custom and my iso directly is in sdb4 because I boot from sdc which then is hd0, and then sda is hd1 & sdb is hd2.

```
 menuentry 'Live ISOs' {
 configfile (hd2,4)/iso/livecdimage.cfg
} 

```Configfile is just more entries. It also is gpt partitioned so I have to have an entry telling it to load the gpt module.

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

menuentry "Ubuntu 13.04 Raring ISO 64bit" {
    set isofile="/iso/raring-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.10 Quantal ISO 64bit" {
    set isofile="/iso/ubuntu-12.10-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "" {
set root= 
}

menuentry "Ubuntu 12.04 Secure Remix ISO 64bit" {
    set isofile="/iso/ubuntu-secure-remix-12.04-64bits.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}


```

---

### Post by GameX2 on 2012-12-22
> From grub /home/gamex does not exist as that is mounted by Ubuntu later,  unless gamex is your user id and the ISO is at the top level in your  home. 
I just find it easier to use directories that grub sees by default. So I use /boot/iso or mostly folders on other drives.

Oh, then that's logical, didn't thought about it.  Usually, I store them in /boot/iso, but I lacked space on " / ",  so I stored this on Home, now.

Thanks for all the infos, I'll try again and keep you in touch.
As for the backup, I'll have to save /etc/default/grub  and  /etc/grub.d/ .

Thank you very much!

---

