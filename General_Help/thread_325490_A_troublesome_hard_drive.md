---
title: "A troublesome hard drive"
date: 2006-12-25
forum: General Help
---

### Post by Hydrargyri on 2006-12-25
Hello!

I am having trouble starting up my computer. I am currently working off of my old 6.06 live cd. Essentially, I start up the computer and, after the usual BIOS stuff, it says "Verying DMI pool data...." and stops. I believe this is because in my old computer setup, I had two hard drives, with this one being the secondary. However, do to some irelevant details, I had to remove the first hard drive and leave this one to fend by itself, causing me this problem.

(Information: The drive booted fine while the old one was also in place -- the old one was first installed singularly, with Windows as a 1/2 partition, and then afterwards the remaining portion was turned into Ubuntu 6.06. That drive was PATA. This one is SATA, and all of it is to 6.10. I had not manually modified any files related to booting at any time. The motherboard is relatively new, and the BIOS was never modified since purchasing last July.)

I did some searching on google and in here, and it seems that I need to change some GRUB file or boot file or something. So, I would like to know if anyone could help me and tell me what files I should modify, what in them should be changed, and also how I can access the files on the hard drive. From this live CD, I can see the hard drive, but it says I cannot mount it or otherwise read it, even.

Thank you very much! :)

---

### Post by Patrick-Ruff on 2006-12-25
looks to me like it's something within your BIOS settings.  I just can't see anything else really . . . if it gives you this error in BIOS, and not when attempting to boot ubuntu, then the error is in your BIOS (i.e. settings, peripherables, etc.)

---

### Post by Hydrargyri on 2006-12-25
Oh, okay. When I was trying to solve this problem myself, I had, in one attempt, manually went to the boot options menu and selected the hard drive. I had also, even before then, told it to check for all hard drives, and it had found the hard drive. To be honest, I'm not too familiar with BIOS -- I know only what it tells me. Is there something in particular I should find or do?

Thanks again!

---

### Post by Azakus on 2006-12-25
Have you done a BIOS update recently? I've noticed that if I do a BIOS update, it screws with the boot order of the drives (as in the PATA drives supercede the SATA drive, which is the one I boot from). I would go into your BIOS and make sure your SATA drive is designated to boot first. If you can't find any problem, flash your CMOS by clicking the jumper (or pulling out the battery, but I'd do that as a last resort). Your motherboard's manual should show you where the CMOS jumper is (it's usually a red switch or clip).

---

### Post by Hydrargyri on 2006-12-25
Well, as I had said before, I had not updated the BIOS at all at any time. Also, I tried what you said, verified that it detected the SATA hard drive (and the optical disc drive, but that was secondary), and did the whole CMOS jumper thingy. Still, it is constantly verifying DMI pool data...

Is there another problem that could be it? Is there a way where I can at least see the files on my hard drive?

Thanks

---

### Post by Azakus on 2006-12-25
Hmm. It can't be "constantly verifying DMI data" because that step takes less than 1 second and the motherboard would be screaming out POST beep codes at you if it got stuck. Can you access your harddrives at all? Post the output of ```
sudo fdisk -l
```

---

### Post by Hydrargyri on 2006-12-25
I think that my motherboard may not be beepyful. I say that because I had a problem (unrelated and since solved. :D) where I had not put RAM in, causing it to not go. I was told that they are supposed to beep when faced with lack of RAM, but no beeps. :S

Anyways...

```
Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23754   190803973+  83  Linux
/dev/sda2           23755       24321     4554427+   5  Extended
/dev/sda5           23755       24321     4554396   82  Linux swap / Solaris

```

---

### Post by Azakus on 2006-12-25
At least it sees your harddisk. Try this
```
sudo mount /dev/sda1 /mnt/disk
```
That should allow you to see the files on the disk.
Then paste the output of your grub boot file
```
cat /mnt/disk/boot/grub/menu.lst
```

---

### Post by Hydrargyri on 2006-12-25
Thank you again, and here is the information:

```
ubuntu@ubuntu:~$ cat /mnt/disk/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=851e2336-f38f-49d2-9d3e-e69d92ca3052 ro
# kopt_2_6=root=/dev/sda1 ro

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
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, kernel 2.6.15-27-386 (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, kernel 2.6.15-26-386 (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, kernel 2.6.15-23-386 (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdc2.
title           Ubuntu, memtest86+ (on /dev/hdc2)
root            (hd0,1)
kernel          /boot/memtest86+.bin
savedefault
boot

```

---

### Post by Azakus on 2006-12-25
There's the problem. It looks like it's trying to boot grub off of a disk that doesn't exist! Replace all (hd1,0) with (hd0,0) and try to boot.

---

### Post by Hydrargyri on 2006-12-26
Sorry for the late update -- the internet connection went down and I also needed sleep.

Anyways, I've done as you suggested, but it still stops at "Verifying DMI pool data...".

I looked over the file thing myself (I'm not very knowledgeable about GRUB) and did some more googling.

The fact that I first installed 6.06 on a since-removed hard drive does not matter, right? I read of some instances where GRUB was not installed on the second hard drive for that reason. I assume because this menu.lst file exists, so does all of GRUB on this hard drive.

Also, I looked at the  list options, and every one but the first pertained to the since-removed hard drive. Should I delete them? Is there another file that also needs to be changed? Or (because you've helped me far too much. :)) is there an online resource that may address all of my questions?

Thanks!

---

### Post by Azakus on 2006-12-26
OH! I didn't see that you had installed grub on a different harddrive than you have now. That means that you don't have an MBR on this drive, which means that it won't boot anything at all. Run this command```
sudo grub-install
```

---

### Post by Hydrargyri on 2006-12-26
Oh, sorry about that. :oops:

When I type in sudo grub-install, it asks to specify a directory. Because I'm working off a live CD, I guess I should choose /mnt/disk/something, but I don't know what the something is. It says it needs a device -- is "sudo grub-install /dev/sda1" the right thing? I'm hesitant to try, seeing as GRUB scares me. 0_o

---

### Post by Azakus on 2006-12-26
/dev/sda1 should work just fine.

---

### Post by Hydrargyri on 2006-12-26
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

Uh oh. This sounds like a bad thing. I mounted the drive correctly beforehand, so its not like it can't see sda1.

---

### Post by bulldog on 2006-12-26
Use (hd0) instead of sda.

The whole procedure to reinstall GRUB to the Sata disk.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

This should work if you only have the Sata as a master boot device enabled,and disabled the IDE disk.

---

### Post by Hydrargyri on 2006-12-26
Thank you both, GRUB is loading.

However, I think that my computer is somehow plotting against me, because there are still a few problems. :(

I still get the old selection -- I could in theory choose OSes and partitions from GRUB that were on the removed disk. However, when faced with that choice, I simply choose the default, right one, and Ubuntu starts to load. So I don't think that's a real problem.

However... before, I had a video card, with the xorg stuff configured to that. Now I'm relying on onboard video. I'm comfortable with changing the settings and everything, from the command line prompt and stuff, so I have no questions there. However, when it says "xorg error", etc., as expected, I also expect it to go to the command line. It does not. It simply has a single, blinking line on the top right (frighteningly like in Jurassic Park when the restarted the computers). Is there some key combination I need to press?

Thanks! :)

---

### Post by bulldog on 2006-12-26
Try CTRL + ALT + F2 and login there.

---

### Post by Hydrargyri on 2006-12-26
Ah! That did it, thank you, Bulldog and Azakus!

But my theory that my computer is out to get me is confirmed. The xorg error is remarkably persistent. Before, I had a PCI-E video card, but now I'm relying on onboard video. I ran sudo dpkg-reconfigure xserver-xorg, but it seems to just stick with the defaults, going for PCI:2:0:0 or something like that, which I have a very good feeling is wrong. Any resources that could help me?

Thank you again!

---

### Post by Azakus on 2006-12-26
{EDIT}Oops. Didn't see sudo there. Nevermind that.
Try this one.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Hydrargyri on 2006-12-26
Oh, thank you, but I figured out the pci channel for the onboard video, and now have my fully working, graphics-running, hard-drive ubuntu again!

Thank you both very much, again. :)

---

### Post by Azakus on 2006-12-26
Glad you got it working again!

---

