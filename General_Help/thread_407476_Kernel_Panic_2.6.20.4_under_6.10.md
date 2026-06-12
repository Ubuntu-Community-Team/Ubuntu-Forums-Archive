---
title: "Kernel Panic 2.6.20.4 under 6.10"
date: 2007-04-12
forum: General Help
---

### Post by Bluesbrother on 2007-04-12
Hi!

This is the first thread I'm writing (usually I find all the answer here without writing myself) and therefore the unprofessional style :-)
Last night Kubuntu made an automatic update wich included a kernel update. This morning I booted , but crashed. This is the boot:
starting up...
Uncompressing Linux... OK, booting the kernel
[      0,118168] PCI: BIOS Bug:MCFG area at e0000000 is not E820-reserved
[      0,118276] PCI: Not using MMCONFIG
[      1,134604] Kernel panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)
[      1,134713]_

And there it's stuck. The same kind of message if starting with recovery.

Obviously it's some kind of problems with my partitions. These are my partitions:

Disk /dev/hda: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1               1        3355    26949006    7  HPFS/NTFS
/dev/hda2   *        3356        8837    44034165   83  Linux
/dev/hda3            8838        9092     2048287+  82  Linux växling / Solaris
/dev/hda4            9093        9729     5116702+   c  W95 FAT32 (LBA)

And this is my menu.lst:

title		Ubuntu, kernel 2.6.20.4 Default
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro quiet splash noapic nolapic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.20.4 Default (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro single
boot

title		Ubuntu, kernel 2.6.20.4.old Previous
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hda2 ro quiet splash noapic nolapic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.20.4.old Previous (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz.old root=/dev/hda2 ro single
boot

title		Ubuntu, kernel 2.6.20.4.old
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20.4.old root=/dev/hda2 ro quiet splash noapic nolapic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.20.4.old (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20.4.old root=/dev/hda2 ro single
boot

title		Ubuntu, kernel 2.6.20.4
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20.4 root=/dev/hda2 ro quiet splash noapic nolapic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.20.4 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20.4 root=/dev/hda2 ro single
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

As you see there's a bunch of 20-kernels. One reason may be that I failed to compile the kernel manually a while ago. 2.6.17 is working fine. Any expert out there who know what to do?

---

### Post by Kay The Bantu on 2007-04-12
hi i've just managed to recover from such a problem, there isn't a clear cut answer but some suggestions.

1. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

2.[http://www.shahidhussain.com/wordpress/index.php?p=33]("http://www.shahidhussain.com/wordpress/index.php?p=33")

these two will show you how to reinstall grub to the MBR coz most probably that is the issue 

try those and tell me what happens.

---

### Post by gbesso on 2007-04-12
The 2.6.20 kernels tend to change IDE drives to /dev/sda instead of /dev/hda
Try changing GRUB to mount the root partition on /dev/sda2 instead of /dev/hda2 
It might not be that, but it can't hurt!

---

### Post by Bluesbrother on 2007-04-12
Hi again!

Kay The Bantu, i tried to just reinstall GRUB on hd(0,1) but no impact.

gbesso, I'm no pro with Linux, but according to fdisk -l, are all my partitions dev/hda

Disk /dev/hda: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1               1        3355    26949006    7  HPFS/NTFS
/dev/hda2   *        3356        8837    44034165   83  Linux
/dev/hda3            8838        9092     2048287+  82  Linux växling / Solaris
/dev/hda4            9093        9729     5116702+   c  W95 FAT32 (LBA)

---

### Post by Bluesbrother on 2007-04-12
> **Bluesbrother said:**
> Hi again!

Kay The Bantu, i tried to just reinstall GRUB on hd(0,1) but no impact.

gbesso, I'm no pro with Linux, but according to fdisk -l, are all my partitions dev/hda

Disk /dev/hda: 80,0 GB, 80026361856 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1               1        3355    26949006    7  HPFS/NTFS
/dev/hda2   *        3356        8837    44034165   83  Linux
/dev/hda3            8838        9092     2048287+  82  Linux växling / Solaris
/dev/hda4            9093        9729     5116702+   c  W95 FAT32 (LBA)

Hmm.... when I think about it. When I'm using kernel 2.6.17 the partition are set to /dev/hda but maybe not in 2.6.20... so how do I install GRUB to sda(0,1)?

---

### Post by gbesso on 2007-04-12
That's what I meant :)
You don't have to reinstall grub, you just need to edit the boot commands.

Here's how you do it:
When GRUB loads, have the 2.6.20 kernel selected and press e.
Click the down arrow key to get to the line that says kernel /boot/vmlinuz (or something similar, basically, the line that starts with kernel) and click e again.
Change the root=/dev/hda2 part to root=/dev/sda2
Click enter and you should be back at the main editing menu, now click 'b' to boot the kernel.
If it boots, great, it works, now you just have to edit your menu.lst to reflect that change as well (the way I explained only works for one boot, but it won't break your old kernel if it doesn't work)
just look for the lines that say kernel /boot/vmlinuz root=/dev/hda2 ro quiet splash noapic nolapic in your menu.lst, and change it to kernel /boot/vmlinuz root=/dev/sda2 ro quiet splash noapic 
nolapic


Good luck, let me know if you need further help.

---

### Post by Bluesbrother on 2007-04-12
Tanks! ...but I'm afraid it didn't solve anything :( same problem as before.  

[ 0,118168] PCI: BIOS Bug:MCFG area at e0000000 is not E820-reserved
[ 0,118276] PCI: Not using MMCONFIG
[ 1,134604] Kernel panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)

Any idea?

---

### Post by gbesso on 2007-04-12
Hmm, did you compile the kernel yourself or did you get a .deb from somewhere?
As far as I know Edgy uses 2.6.17, so the automatic upgrade must have been from a non-official repository.
Could you paste your /etc/apt/sources.list?

---

### Post by Bluesbrother on 2007-04-12
The first  time I compiled the kernel, I downloaded it from kernel.org and followed a guide. Then nothing happend. Yesterday it went via updates in Adept.

My sources.list

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free 
# 
# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted 


deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted 

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

---

### Post by gbesso on 2007-04-12
Do you have a file called initrd.img-2.6.20-4 or something similar in /boot?
Basically, an initrd file that fits the 2.6.20 kernel?

---

### Post by Bluesbrother on 2007-04-12
No, only for 17-0 and 17-11! Can I just download it and put it there?

---

### Post by gbesso on 2007-04-12
Umm no that's not a good idea, but it's very likely the cause of the kernel panic.

Boot your 2.6.17 kernel and do this:
sudo update-initramfs -c -k 2.6.20.4 
(if it says something like Cannot find /lib/modules/2.6.20.4, go to /lib/modules and look for a directory that is similar to 2.6.20, and use that directory's name as the -k parameter, say you have /lib/modules/2.6.20.4-generic :
sudo update-initramfs -c -k 2.6.20.4-generic

Also, the installation of the kernel usually does that by itself, so the fact it hasn't makes me wonder if you might've removed the initramfs-tools package by accident, so if the commands i mentioned above don't work:
sudo apt-get install initramfs-tools

Good luck!

---

### Post by RJARRRPCGP on 2007-04-12
Did you recently add a RAM module and didn't remove the others? If you did, it likely caused the OS to silently get corrupted. 

Modern motherboards are a suspect for data corruption with more than one RAM slot used.  

I, not too long ago, after just turning on one of my PCs with Windows XP or Windows 2000, which has all three SDRAM slots filled, gotten the dreaded STOP: 0x0000007B INACCESSIBLE_BOOT_DEVICE BSOD. 

But that may have been caused by CMOS corruption, thus I recently changed the CMOS battery on that motherboard.

---

### Post by Bluesbrother on 2007-04-13
> **gbesso said:**
> Umm no that's not a good idea, but it's very likely the cause of the kernel panic.

Boot your 2.6.17 kernel and do this:
sudo update-initramfs -c -k 2.6.20.4 
(if it says something like Cannot find /lib/modules/2.6.20.4, go to /lib/modules and look for a directory that is similar to 2.6.20, and use that directory's name as the -k parameter, say you have /lib/modules/2.6.20.4-generic :
sudo update-initramfs -c -k 2.6.20.4-generic

Also, the installation of the kernel usually does that by itself, so the fact it hasn't makes me wonder if you might've removed the initramfs-tools package by accident, so if the commands i mentioned above don't work:
sudo apt-get install initramfs-tools

Good luck!

I could create the initrd, but it doesn't change a thing. I think I've messed it up to badly while trying to compile the kernel myself. Maybe I'll just install the 7.04 when the stable version are released instead... if you don't have more trix up your sleves :D

---

### Post by gbesso on 2007-04-13
I'm out of tricks, I'm afraid :(
However, Feisty will be out in less than a week, so unless you really need 2.6.20 right now, it's probably worth the wait :)

---

### Post by Bluesbrother on 2007-04-13
Thanks for trying! I have no trouble with 2.6.17, except my wlan isn't working. I go for Feisty! Thanks again!

---

### Post by gbesso on 2007-04-13
You're welcome, sorry I couldn't solve it!
Have you tried ndiswrapper for the wlan?

---

### Post by Bluesbrother on 2007-04-14
Yes I've tried everything. My w-lan card is supposed to be supported by the kernel, but during the installation of Edgy, the system was unable to at all detect a network card. Hope Feisty will solve it.

---

