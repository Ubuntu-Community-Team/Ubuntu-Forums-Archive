---
title: "Unable to boot after installing Ubuntu 12.10 alongside Windows 8"
date: 2013-03-11
forum: General Help
---

### Post by DJLamar on 2013-03-11
I've been at this for hours and have looked through tons of forum posts without finding anything quite matching my situation.

I started off trying to follow these instructions:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

including using Ubuntu 12.10, disabling quick boot, and disabling secure boot.

The installer couldn't detect what space was used or not in the Windows partition (and gparted sort of just freaked out when I tried it), so I used Partition Wizard in Windows to shrink that partition. After that the installer (from USB) gave me the option to install alongside the other OS(es, it thought there were multiple) and it correctly used the large, unformatted one left over from the shrink.

After that, on restart the manufacturer logo shows for a split second before I get a black screen with "Operating system not found." I can get into the BIOS/EFI and boot from USB, but even the EFI's option for loading Windows just results in the "Operating system not found" screen.

I tried boot repair twice as the instructions said. The link that it gives is here: [http://paste.ubuntu.com/5606688/](http://paste.ubuntu.com/5606688/) The result is still the same.

So basically, I can't access Windows or Linux, I can only boot from USB stick. This is on a Sony Vaio S series. Any help would be greatly appreciated.

---

### Post by oldfred on 2013-03-12
Your are showing the /mapper which is RAID. So this is an UltraBook with Intel SRT which uses RAID.

Boot-Repair tries to add the RAID drivers to work as the standard desktop does not have the RAID drivers.

       Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

The UltraBooks are often have dual video. so Bumblebee is usually the solution.
While a Dell, Intel is a standard for all systems

 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

### Post by DJLamar on 2013-03-12
Hmm, you are right that this computer has RAID, but it's not SRT exactly, rather it's just two big SSD drives joined together with RAID 0. The installer seemed like it was able to see the partitions correctly (while those posts say the installer couldn't tell the partitions apart, just saw the drives themselves), and I can read the partitions correctly from the live USB, but I'll poke around with the information from those posts and see if I can get anywhere.

---

### Post by oldfred on 2013-03-12
Hope you have good backup plans. With RAID 0 you lose both drive's data if one fails. RAID 0 is for speed, but with SSDs I do not know that you really get that much more anyway. 

 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by DJLamar on 2013-03-12
Yes, I know about RAID 0's failure problems, but I doubt the failure rate for an SSD drive is significant enough to cause big problems, especially when its just two of them joined together. The computer came with RAID 0 set up, so I assume Windows etc. are set up across it and that it could be a big headache to disable. Plus, I'm a data mining/machine learning researcher and sometimes use 100 GB+ data sets, so keeping the boost in speed could be nice :)

I had typed up this post just as you replied:

One note: I checked the installer again and it actually detects each  partition (and its file system type and size, but not its used space or  what OS is on it) correctly but lists each of them twice. In the drop  down box for selecting a device for boot loader installation, I again  see each partition two times, but there it clarifies a little more.  mapper/...Volume0 is listed as Linux device-mapper (striped) (512.1 GB,  the total size of the RAID array), then the partitions (with the OS or  purpose) in physical order (i.e. the Linux root and swap partitions  before one of the Windows recovery partitions, since I created the Linux  partition in between), then it lists all of the partitions again in  order of partition number with the detected OS and the note "Linux  device-mapper (linear)."

Two questions:
1) If I scrub the RAID metadata using  dmraid -rE /dev/sda before installing, would that have any adverse  effects since the existing Windows installation is presumably already  striped across the disks?
2) I just noticed that the default option  in the installer for the boot loader installation is listed as /dev/sda,  not the Volume0 drive which seems to map to the striped RAID array  considering its size. What's the worst that could happen if I install  with Volume0 as the boot loader installation target? (I'm paranoid  because I have to use a button on the computer to start into this  Vaiocare screen to access the BIOS, so I'm not sure where the line is  between the things hard-coded into the motherboard/firmware and the  things that I could accidentally destroy.)

---

### Post by oldfred on 2013-03-12
I do not know enough about RAID to really help.

I do not think you want to break the RAID array if you want to keep Windows in the RAID.

With 12.04 you have to use the Alternative installer to install to RAID (or the server installer).

But they did away with the alternative installer with 12.10.

       Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

---

### Post by DJLamar on 2013-03-12
Ok, I feel like I'm getting somewhere now, thanks for the help so far.

I guess I could try using the 12.04 alternate installer. Once I just get something set up I don't think it should be a problem to upgrade from that if I want.

My worry at this point is that I may have already somehow borked the Windows installation when I installed Ubuntu the first time. I tried just reinstalling it, specifying the particular duplicate of Volume0p7 that seemed to correspond to the striped option, and it just told me there was an error creating the swap space (which was already created with the first Ubuntu install attempt) and quit. But I guess I have access to the Microsoft's MSDNAA software if I need to reinstall Windows for any reason...

I'll see how this alternate installer goes now...

---

### Post by DJLamar on 2013-03-12
Ok, I used the alternate installer. I think it didn't use the EFI bootloader when installing grub though. I installed grub there to Volume0 (the whole virtual disk as controlled by RAID) and still got OS not found. So then I booted the live CD of the desktop (not alternate) 12.04 64 bit Ubuntu, installed grub-efi, mounted p7 (Ubuntu) as /mnt and p3 (one of the two EFI partitions, the one that some partition editors have been calling Windows 8 even though it's just the loader for Win 8) as /mnt/boot/efi, then I mounted proc, dev, sys, dev/pts to their respective subdirectories in /mnt with -o bind, chrooted to /mnt, and did apt-get install grub-efi there (tried grub-install right after that but from the output that seemed redundant, ha). Got the error "[COLOR=#000000][FONT=Helvetica]ERROR: mkdir /var/lock/dmraid" at one point in the apt-get install but otherwise no errors (I have the rest of the output from those saved if anyone wants them).

This didn't work either, so I tried boot-repair with the default settings, pastebin here: [/FONT][/COLOR]http://paste.ubuntu.com/5609030/
[COLOR=#000000][FONT=Helvetica]
So then I tried boot-repair again with p1 as the EFI instead of p3: [/FONT][/COLOR]http://paste.ubuntu.com/5609058/
[COLOR=#000000][FONT=Helvetica]
Still no luck, so I ran boot-repair using its option to just restore the MBR, but this *still* doesn't work: [/FONT][/COLOR]http://paste.ubuntu.com/5609069/
[COLOR=#000000][FONT=Helvetica]
In the pastebin in the original post, there was no MBR detected at all on Volume0, the main controller. In these last few at least there's an MBR detected in the right place.

I also found a blog post by a guy who has almost exactly the same computer as me and wanted to do the exact same thing I'm trying to do, who succeeded: [/FONT][/COLOR][http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
(just about the only steps in that pipeline that I having tried are doing the Windows 8 recovery disk repair and the manual moving around of some of those files to give the grub files the same locations as the windows files had)

[COLOR=#000000][FONT=Helvetica]Only problem is that I don't have a Windows 8 disk. My Recovery partitions both seem to be fully intact and readable though -- does anyone know if/how I can maybe make the disks from that while booted from the live USB?[/FONT][/COLOR]

---

### Post by oldfred on 2013-03-12
Not sure you can make Windows recovery from Linux.

If you have access to another Windows 8 machine:
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Windows also should have a backup of its efi file and maybe you can just copy it into the efi partition and boot? It will also need a BCD.
Ubuntu mounts the efi partition at /boot/efi.

 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi


 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.


Some notes I have saved, but not sure what applies as I do not have Windows:

 Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx")
rem === Copy boot files to the System partition =========
W:\Windows\System32\bcdboot W:\Windows /s S:
\Windows\Boot\EFI

      
 Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
How UEFI works in Post #76 - skodabenz  thread by Avidanborisov
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

---

### Post by DJLamar on 2013-03-12
Haven't tried copying over the old files yet. I did get ahold of a Windows 8 CD (through MSDN academic alliance) and started that up. The automatic repair utility couldn't figure out what the problem was and the reset, refresh, etc. complained about the proper partition either being missing or locked. Even in the command line I couldn't detect any partitions -- it seems Ubuntu has no problem figuring anything out, but Windows can't read anything. Maybe if I could fool the reset utility into thinking that an external hard drive is the recovery partition I could have some luck.

I also tried just running the Windows 8 installer and wiping everything and starting over. But then the installer complains that it can't find a media driver that the computer needs (saying it probably has to do with USB, CD, DVD, or something).

The guy in the blog post I linked to who has the same computer mentions that he was able to get Ubuntu installed and running in Legacy mode. Maybe I'll just try wiping the whole hard drive and doing that to get Ubuntu on the machine while I wait for recovery disks from Sony to come in the mail.

---

### Post by DJLamar on 2013-03-13
So I had an epiphany while trying to sleep last night about what was going on when I had the windows 8 CD loaded up. It couldn't detect any partition or hard drive (but could find usb and cd just fine) and aborted installation due to lacking a media driver... Because it probably didn't come with a raid driver. Probably if I can put the right driver on usb I can load it from command prompt while in the windows CD and the automatic boot repair might work. I'll try this in a while today.

---

