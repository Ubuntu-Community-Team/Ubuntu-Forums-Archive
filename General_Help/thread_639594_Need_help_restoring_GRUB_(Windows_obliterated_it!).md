---
title: "Need help restoring GRUB (Windows obliterated it!)"
date: 2007-12-13
forum: General Help
---

### Post by midir on 2007-12-13
Okay, bit of background. I installed Kubuntu earlier this year and eventually got it working okay and I was very happy with it. But a few months back Windows was going wrong so I had to reinstall that. As I had feared, Windows obliterated GRUB and replaced it with a simple stub that boots NTLDR. So for ages now I haven't been able to boot into Ubuntu at all. :-(

Today I decided I'd had enough of it and I've been trying to fix it. But it's an absolute nightmare, I just don't know what to do, and I'm scared of damaging something. Hopefully there's somebody out there brainy enough to help. I'm not very good with Linux and even less skilled with the Linux shell.

Basically what I did was I booted up on the CD and selected the Rescue a broken system option and got to the bit about reinstalling GRUB. But it doesn't work. It just says it's failed.

By complete accident I noticed that pressing Alt+Left/Right from the installer took me into a set of extra screens and into a basic shell. So I've been discovering the Linux terminal and stuff from this. I tried running "grub-installer hd0" and "grub-installer /dev/hda1" and "grub-installer /dev/sda" and various things like that but again it just complains. Something about it not being a block device or something (?). I can't remember exactly but if the error message is important I'll do it again and write it down.

By exploring the in-memory filesystem from the shell I got when I pressed Alt+Right I discovered the /proc/partitions file, which contains the following info:

```

major  minor    #blocks  name
8          0  244198584  sda   
8          1  244196001  sda1
8         16   80043264  sdb
8         17   60034903  sdb1
8         18   10337827  sdb2
8         19          1  sdb3
8         21    9215608  sdb5
8         22     446512  sdb6
```

sda (why isn't it hda?) is the main drive. It's got 1 single 250GB partition [noparse](C:)[/noparse], formatted as FAT32, containing Windows 2003 R2 in C:\WIN2003. It's got the usual NTLDR and BOOT.INI stuff.

sdb is both my file backup drive and the one where I installed Ubuntu (because I was scared about partitioning the main drive). sdb1 is the D: drive. sdb2 is the E: Drive. I'm not sure what sdb3 is. sdb5 is the Ubuntu root partition (ext3), and sdb6 is the swap partition.

I also ran fdisk -lu because I remembered reading about it somewhere on these forums. This is the output:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         Emd     Blocks   Id  System
/dev/sdb1           16065   120085874   60034905    c  W95 FAT32 (LBA)
/dev/sdb2       120085875   140761529   10337827+   c  W95 FAT32 (LBA)
/dev/sdb3       140762222   160086527    9662153    5  Extended
/dev/sdb5       140762223   159193439    9215608+  83  Linux
/dev/sdb6       159193503   160086527     446512+  82  Linux swap / Solaris
```

The rescue option also gave me the chance to boot into a shell on /dev/sdb5. I did this (first time I've been into that partition in quite a while) and checked /boot/grub and it already contains everything it should. There's no reason it shouldn't anyway, the only thing that's missing is the GRUB boot stuff on the other, C: drive.

Other information:
- I can't boot the Ubuntu LiveCD because it's not compatible with my system (memory error or something), so I've always used the alternate CD. If it helps, I have a PCLinuxOS 2007 CD that does boot straight into a live desktop.
- I tried following this stuff: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm). It's all a bit above me I'm afraid.

So that's as far as I've got. Can anyone help me in persuading GRUB (or LILO, or whatever) to put itself back into the MBR, so that I can boot Linux again?

---

### Post by forestpixie on 2007-12-13
have you tried to use the supergrub livecd - worked for me first time. Download, burn as an iso and boot with it - docs at the website

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Irony on 2007-12-13
Use the PCLOS live disc - go to synaptic to see if grub is installed, if it is not then install it, then go to terminal and do;

```
su

grub
```

This opens up the grub program, with a prompt of grub>, now type;

```
find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit
```

This installs grub to point at hda3, substitute where you want it to point, e.g. sdb5

Here in detail is the output;

```
grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)
 (hd0,8)
 (hd0,11)
 (hd1,1)
 (hd1,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit
```

---

### Post by strabes on 2007-12-13
This is really easy. See the link in my signature.

---

### Post by midir on 2007-12-18
Sorry for not replying to my own thread for a while - I was away from the computer for a few days.

I tried Irony's suggestion first as it seemed the simplest. I was terribly scared I was gonna break something and then it wouldn't boot at all, but it worked first time! :D :D :D I had to change it to *root (hd1,4)* on my system, but that was what the *find* command gave me, so it wasn't too hard.

As an unfortunate side-effect the /etc/fstab file seemed to get overwritten (maybe ?? is that possible ?) which meant that fsck turned up again - something which I remember caused all sorts of problems when I first installed Linux because it went at a phenomenally sluggish crawl while it sat there checking the FAT partitions. Fortunately I'd dealt with this before so I knew how to disable it.

All is working again. Thank you for your help everyone. :)

---

### Post by forestpixie on 2007-12-18
excellent glad you're back - can you mark thread solved then :)

---

