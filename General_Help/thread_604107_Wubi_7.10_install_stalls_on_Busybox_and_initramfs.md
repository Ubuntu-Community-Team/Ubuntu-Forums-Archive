---
title: "Wubi 7.10 install stalls on Busybox and initramfs"
date: 2007-11-05
forum: General Help
---

### Post by jldindc on 2007-11-05
First time trying Ubuntu here, so go easy on me:

Installing on: Thinkpad T60 laptop
2 GB RAM, WinXPPro on C: which is NTFS
CDROM is D:
Blank 10GB partition E: which is FAT32

I tried to install Wubi 7.10 alpha-383 from the C: drive onto E:, using a downloaded desktop iso placed in the same directory as the wubi install file.
Install seemed to go fine until what seemed like the final reboot, at which time I get the black Ubuntu splash screen, then it goes all black with just this on the screen:
[B]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)[/B]

Is this hang here due to the fact that I tried to install to a partition other than my C: drive?  I'm guessing tihs is the case, but want to check.
Thanks.

---

### Post by ago on 2007-11-05
1. edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "debug"
3. reboot
4, at the command line type "cat /tmp/*.debug" <enter>
5. there should be an error in the latest few lines, post it here.

---

### Post by jldindc on 2007-11-05
I went ahead and edited 
E:\ubuntu\disks\boot\grub\menu.lst
and replaced "quiet splash" with "debug" (without quotes)
I rebooted, but it still hangs at the same Busybox/initramfs prompt.
It doesn't get to a command line.

Is this because I installed to the E: drive, which is the same physical drive as the C: drive?  (both C: and E: are primary partitions).
Thanks.

---

### Post by ago on 2007-11-06
Normally you can type things at the Busybox/initramfs prompt

---

### Post by ago on 2007-11-06
You may have to wait up to 5 minutes in some cases.

---

### Post by jldindc on 2007-11-06
Thanks for your reply.

I typed "cat /tmp/*.debug" at the initramfs prompt, but it came back with "no such file or directory exists" if I have that working correct.
I then waited about 5 minutes. Still nothing.

Should I try installing again?

---

### Post by dadani on 2007-11-06
> **jldindc said:**
> Thanks for your reply.

I typed "cat /tmp/*.debug" at the initramfs prompt, but it came back with "no such file or directory exists" if I have that working correct.
I then waited about 5 minutes. Still nothing.

Should I try installing again?

Yes, and don't type "cat /tmp/*.debug"
type "cat /tmp/initramfs.debug"

---

### Post by javacasm on 2007-11-06
I got the same error.
Looking at  /tmp/initramfs.debug
find an "Invalid argument" in  "mountt -r -t vfat /dev/sda2 /root"
the partition is correct an got the same error when try to mount any other partition (vfat, ext3, ntfs, penn drive) or using partition name, id or uiid
Any clue?

---

### Post by dadani on 2007-11-06
format your harddrive and take no FAT oder FAT32. I had, a error of this kind, my problem soulution was to fromate the HD in NTFS, maybe then it will work ;)

---

### Post by dadani on 2007-11-06
format your harddrive and don't take FAT or FAT32. I had, a error of this kind, my solution of this problem was to fromate the HD in NTFS, maybe then it will work ;)

---

### Post by javacasm on 2007-11-06
I use wubi because I don't want to format my hard drive.
Reformat is not an option.

---

### Post by dadani on 2007-11-06
i think there is a problem with FAT HDs, it works brilliant after a reformat (then NTFS) ;) sry that was my solution, but maybe you have a usb hd with (NTFS) and then you can test to install your Wubi stuff there. Or use a VMware Player ;)

---

### Post by ago on 2007-11-06
> **javacasm said:**
> I got the same error.
Looking at  /tmp/initramfs.debug
find an "Invalid argument" in  "mountt -r -t vfat /dev/sda2 /root"
the partition is correct an got the same error when try to mount any other partition (vfat, ext3, ntfs, penn drive) or using partition name, id or uiid
Any clue?

Can't you mount any of the devices /dev/sdX?

---

### Post by jldindc on 2007-11-06
I solved my problem by going back into windows and reformatting my E: partition as NTFS, rather than the FAT32 it was before.  Install into E: partition then worked fine. Thanks for that suggestion.  I already like Ubuntu and it's only been a few hours !

---

### Post by javacasm on 2007-11-07
I cannot mount any of the drives (vfat and ntfs) from a hard disk and from a usb-drive

---

### Post by ago on 2007-11-07
Is that within Ubuntu or at boot? What command are you using?

---

### Post by h1volt3 on 2007-11-07
I have this problem too.
I use the version of Wubi bundled within Xubuntu 7.10 CD, but no matter whether I use the command "Ubuntu-Linux" in Windows bootloader or boot directly from the CD, I still get that BusyBox.
Even when I use the Ubuntu 7.04 CD shipped from Ubuntu website, I still get this problem
But when I use the Xubuntu 6.10 CD, I can even install that version succesfully.
However, I don't want to upgrade from 6.10 to 7.10. It takes too much time. I'm new to Linux, so my *buntu installation is soon to get messed up and I think having a format and fresh reinstall is a nice choice.

I think the problem (in my case) is not harddrive-related, because I have 2 HDDs both formatted in NTFS and Ext3. I disabled each of them and tried to boot Xubuntu 7.10 CD with the other, but still get that problem.

Is there any problem with the installation progress in *buntu version 7.04 and above?

---

### Post by javacasm on 2007-11-07
> **ago said:**
> Is that within Ubuntu or at boot? What command are you using?

I got the error during boot using this command

mount /dev/sda2 /root -t vfat

---

### Post by Bluemercury on 2008-03-03
Im having this problem as well, both harddrives are in FAT32, it seems there's some issue with the FAT32?i thought linux filesystem wast fat or fat32....strange that it works with ntfs......
Anyway should i try to fix this or change the partition type?might as well install it in the c:\ partition which already is in NTFS....

---

### Post by ago on 2008-03-04
Can you pls try to mount your partitions manually from the busybox prompt?

The command will be something like:

modprobe vfat
mount -t vfat /dev/sdaX /root 

modprobe fat
mount -t fat /dev/sdaX /root  

mount -t auto /dev/sdaX /root 

replace X with your fat partition number. Pls report any error you see when running the above commands.

---

### Post by ago on 2008-03-04
Do you use usb sticks/drives by any chance? Can you try disconnecting them?

---

### Post by Who on 2008-04-03
> **ago said:**
> Can you pls try to mount your partitions manually from the busybox prompt?

The command will be something like:

modprobe vfat
mount -t vfat /dev/sdaX /root 

modprobe fat
mount -t fat /dev/sdaX /root  

mount -t auto /dev/sdaX /root 

replace X with your fat partition number. Pls report any error you see when running the above commands.

I am doing this after Wubi has rebooted (second time. It worked the first) for 8.04 beta
I have the issue this thread is about: I get the following result 
FATAL: Module vfat not found.

FATAL: Module fat not found.

I did run all three mount commands anyway to see if the message was the same as when mounting at startup:

first two fail with
mount: Mounting /dev/sda4 on /root failed: No such device

The third
mount: Mounting /dev/sda4 on /root failed: Invalid Argument

And out of interest (I saw you wondering on another thread...)
the /dev/disk/by-uuid/192B-13FD entry _is_ there... I can't mount it though (using commands as above)

Hope that helps - shall I stick it in Launchpad?

---

### Post by ago on 2008-04-03
try to uninstall everything, remove ubuntu-backup and reinstall redownloading the ISO

---

### Post by Who on 2008-04-03
> **ago said:**
> try to uninstall everything, remove ubuntu-backup and reinstall redownloading the ISO

Out of interest, what have you changed?

If it is essential or specifically useful for diagnostics I will (willingly :)) do the whole thing again, but I think, given that I had to sysrq+RSEI then run ubiquity noninteractive and wait for quite a while etc I would like to try any way possible to avoid doing the whole reinstall.

Can you verify: I won't be able to use LVPM if I don't have the space to create a spare partition on the local disk? I hoped there might be a way to do it using a USB disk, but given that I can't boot from USB I feel I might not have any love there (I'm not so knowledgeabout these things - but I wonder whether a crazy combo of copying the disk image on the local disk to usb disk, moving swap to the usb disk, mounting usbcopy of main image, chrooting, unmounting the old one+swapoff, then using LVPM work?). I ask because if I reinstall again I'd quite like it to be my last time - for a while anyway, and if I am ultimately going to use UNetBootIn I might do it this time...)

Thanks for your speedy help. Makes this kind of thing much more fun :)

---

### Post by ago on 2008-04-04
> **Who said:**
> Out of interest, what have you changed?
The issue looks to me as a mismatch between the kernel on C: and the kernel within the ISO.

> I hoped there might be a way to do it using a USB disk, but given that I can't boot from USB I feel I might not have any love there
You can install on USB disk, the bootloader will still be on your fixed disk, hence it does not matter if you cannot boot from USB provided that the USB disks can be "seen" at boot time (by grub4dos), which is normally the case.

---

### Post by Who on 2008-04-05
> **ago said:**
> try to uninstall everything, remove ubuntu-backup and reinstall redownloading the ISO

Well, my computer doesn't have 256mb ram so I didn't use the lates wubi - but I did redownload all the images - I've rebooted twice now :)

Magically my xsetup is correct now too... :D

---

### Post by drynish on 2008-05-23
I solve the issue by shutting down couple of times correctly windows. Maybe when the fs is incorrectly shut down or there is too many errors, it could have impacts on the system.

Thanks and have a nice day ;)

MIchel

---

### Post by ago on 2008-05-24
> **Who said:**
> Well, my computer doesn't have 256mb ram so I didn't use the lates wubi - but I did redownload all the images - I've rebooted twice now :)

Magically my xsetup is correct now too... :D
You can run: wubi.exe --skipmemorycheck
Your luck may vary though

---

### Post by jackhe22 on 2008-05-28
Hey Buddy,

There is a simple but great solution...

edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install!

Enjoy...

---

### Post by zm8@hotmail.com on 2008-06-07
> **jackhe22 said:**
> Hey Buddy,

There is a simple but great solution...

edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install!

Enjoy...


Yup - thanks, this worked for me as well. I had tried quite a few of the other solutions, but no luck.

One thing was that I tried the "edit" command under the  INITRAMFS prompt and didnt work - a not found error. 

What I realised was that I had to edit the script at the bottom of the install page...  quiet splash is towards the end of the script.....

---

### Post by jackhe22 on 2008-06-08
Edit E:\ubuntu\disks\boot\grub\menu.lst - Replace quiet splash with all_generic_ide !

---

### Post by jmjohn on 2008-06-14
Hey Folks,

I had the same problem: initramfs prompt instead of Xubuntu.

But my menu.lst file was not located at the location that others specified in these directions:

[INDENT]edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install!
[/INDENT]

Instead, it was located at: c:\ubuntu\install\boot\grub\menu.lst

and I changed it as above and figured, hey, I'll copy it to c:\ubuntu\disks\boot\grub\menu.lst .  So I did so, putting it in both places, just to be sure.

And it worked--but I have a serious video card problem so it actually didn't work.

Peace,
jmjohn

---

### Post by justifiedandancient on 2008-07-10
I have the same problem on an IBM ThinkPad Z60m. I had a perfectly working Wubi installation and saved it to a USB drive as I had to re-install the Windows underneath (it belongs to work and not my department!). After the re (Windows) install, I copied back the Wubi installation and re-patched boot.ini. Now windows boots fine and Ubuntu dumps me in initramfs where I can mount the underlying NTFS drive. Having replaced the quiet thing with all ide one I get the following error during:

/build/buildd/linux-2.6.64/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Done.
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/E4640FA0640F7498 does not exist. Dropping to a shell!

BusyBox blah blah blah.

Implies that the hard disk has changed it's UID identity which it may well have done. Is there any way I can patch this up so it will boot successfully?

---

### Post by justifiedandancient on 2008-07-10
Obviously, (ahem) I meant the UUID of the file. Now that is configured into the same init file so that if I could determine the UUID of the file I should be able to patch it?
P.S. Mine is an 8.04 install

---

### Post by justifiedandancient on 2008-07-16
Well, answering my own post again! In another thread 457824 here [http://ubuntuforums.org/showthread.php?t=457824]("http://ubuntuforums.org/showthread.php?t=457824") there is a description of how to find the UUID of your disk using a livecd and blkid. Now, I used this and only patched the menu.lst in C:\ubuntu\disks\boot\grub with the "new" UUID (I actually mounted the NTFS partition on the live CD and edited the said file there to save having to boot 'doze again). My previously created Wubi Linux installation now boots again.

I have no idea if this could be used to move Wubi installs between machines though! Of course, as I said originally, this is all using 8.04.

---

### Post by richar75 on 2008-07-16
I had the same problem installing ubuntu 8.04 and kubuntu KDE4 with wubi. 
I have windows XP installed in C: partition (15Gb) as NTFS , and another primary one (NTFS) for data.  I tried installing ubuntu in C. and then when I restart the laptop the ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

My C:/ubuntu/disks/boot/grub/ is empty. I tried booting in windows, checking the partition with the windows tool and restart the machine...but the same error appears.

I don't know what is the problem...we need help! :(

cheers

---

### Post by oldguardjon on 2008-07-16
I have the same problem with Wubi 8.0. If you find an answer I will appreciate a note...Thanks..

---

### Post by smo0th on 2008-07-17
> **oldguardjon said:**
> I have the same problem with Wubi 8.0. If you find an answer I will appreciate a note...Thanks..

from your xp, open cmd and type ```
chkdsk /f d:
``` assuming drive d is where you installed your wubi. Reboot and you should be able to use ubuntu again :)

---

### Post by ago on 2008-07-17
> **richar75 said:**
> I had the same problem installing ubuntu 8.04 and kubuntu KDE4 with wubi. 
I have windows XP installed in C: partition (15Gb) as NTFS , and another primary one (NTFS) for data.  I tried installing ubuntu in C. and then when I restart the laptop the ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

My C:/ubuntu/disks/boot/grub/ is empty. I tried booting in windows, checking the partition with the windows tool and restart the machine...but the same error appears.

I don't know what is the problem...we need help! :(

cheers

Press esc at boot after selecting "Ubuntu" and try the other boot options. Some machines require extra boot parameters (as workarounds) that have to be entered manually such as all_generic_ide or "irqpoll". As mentioned by smo0th, unclean shutdowns are also another common reason.

---

### Post by justifiedandancient on 2008-07-17
> **richar75 said:**
> I had the same problem installing ubuntu 8.04 and kubuntu KDE4 with wubi. 
I have windows XP installed in C: partition (15Gb) as NTFS , and another primary one (NTFS) for data.  I tried installing ubuntu in C. and then when I restart the laptop the ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

My C:/ubuntu/disks/boot/grub/ is empty. I tried booting in windows, checking the partition with the windows tool and restart the machine...but the same error appears.
Before the last problem I also had the error after a bad 'doze shutdown - not that the shutdown appeared bad but Ubuntu wouldn't boot and a chkdsk fixed it.

Have you tried the all_generic_ide fix (see e.g. thread 417961) as that was one of the steps I did to get mine to work although I think I only needed to fix the UUID. Then again, mine was working and only stopped after a re-install of XP. Mind you, your empty grub directory doesn't sound too helpful, mine contains 3 files default, device.map and menu.lst (which is the one I put the all_generic_ide and changed UUID fixes into)

---

### Post by wolfmanyoda on 2008-07-17
> **jmjohn said:**
> Hey Folks,

I had the same problem: initramfs prompt instead of Xubuntu.

But my menu.lst file was not located at the location that others specified in these directions:

[INDENT]edit c:\ubuntu\disks\boot\grub\menu.lst
2. replace "quiet splash" with "all_generic_ide"
3. reboot
4. Ubuntu Install!
[/INDENT]

Instead, it was located at: c:\ubuntu\install\boot\grub\menu.lst

and I changed it as above and figured, hey, I'll copy it to c:\ubuntu\disks\boot\grub\menu.lst .  So I did so, putting it in both places, just to be sure.

And it worked--but I have a serious video card problem so it actually didn't work.

Peace,
jmjohn

I also had it in the location that you did, and I changed it to all_generic_ide and saved to both locations as well. Mine still hangs.
I also tried cat /tmp/initramfs.debug but it gives me "no such file or directory"
Any ideas?

Nevermind, I got it working.

---

### Post by richar75 on 2008-07-22
I was trying with changing the splash to generic_ide, running chdisk before booting and another recipes you post it here, but I didn't get it.
If I find the solution I 'll write it here,
thanks

---

### Post by Charvelguy on 2008-09-08
I have a friend that I am helping and decided to load Ubuntu on a separate partition.
I opted for using Wubi instead as it seemed the install would be quite painless. I'm putting the 8.04 Wubi install on a NTFS partition using 15gb. XP Home is also loaded in the same NTFS format of the drive. There's a couple other small partitions, one for 47mb in FAT and one other for 3.49gb in FAT32.  My friend would like to save XP Home for now instead of writing over it. It is a malware infested XP that  has Xpert Antivirus and a bunch of other trojans, quite nasty. 
The shutdown was not clean, sooo, I'll have to try that first before I do anything else. Its going to be a few days before I'm over at thier home again but I'll post results once I get in front of a screen and can try these suggestions out. Thank you!

---

### Post by speedster239 on 2008-10-17
> **drynish said:**
> I solve the issue by shutting down couple of times correctly windows. Maybe when the fs is incorrectly shut down or there is too many errors, it could have impacts on the system.

Thanks and have a nice day ;)

MIchel

Thank you drynish, this method worked fine. Evidently if you shut the system down by holding the power button down for 10 secs, or by hitting the reset button it causes the system some form of harm which thus causes Ubuntu install via wubi not to boot properly.

In short, just restart windows and it *should* fix your problems.

---

### Post by craigcrawford114 on 2008-10-17
I have this problem. I have tried the "shutdown" and "restart" solutions but with no avail.

Anything else I can try?

---

### Post by ago on 2008-10-17
Wubi 7.10 is not supported please use wubi 8.04 or 8.10

---

### Post by craigcrawford114 on 2008-10-17
I am using 8.10. I still have the same problem with it stopping at "Busybox"

I am on a hardware RAID setup. Could this be the problem?

---

### Post by ago on 2008-10-17
> **craigcrawford114 said:**
> I am using 8.10. I still have the same problem with it stopping at "Busybox"

I am on a hardware RAID setup. Could this be the problem?

Yes that can be, also in the coming days, there have been changes in 8.10 that created boot problems in the past 2 days. So you should use the latest version [http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield) (513+) with today's daily ISO (if you delete your current one, it will be downloaded for you)

---

### Post by Vertigo77 on 2008-10-31
On a generic PC based on Intel G31 (Gigabyte motherboard) with 3 GB RAM, HDD WD 640 GB, ATI 3400 with 256 MB, and a 22" monitor connected over DVI, I've tried to install ubuntu 8.10 with WUBI 8.10, both downloaded today. No matter what option I selected, safe graphics or ACPI workaround I still get the busybox prompt and installation stops. Please advice. If you need more details I will do what you telling me to do :). Thanks.

---

### Post by ago on 2008-10-31
At the busybox type the following commands and post the output

cat /proc/cmdline
cat /proc/mounts
cat /proc/partition
grep err /casper.log
grep mount /casper.log

---

### Post by Vertigo77 on 2008-10-31
You have attached a photo of my monitor with the output that you asked. If you have a more normal way for me to get the output from the command prompt to here I am open to suggestions . 
My HDD is partitioned like this. All partitions are NTFS.
I have a C: drive for boot, an E: drive for swap and a big F: drive for data. I am installing wubi from F and the path for the ubuntu install is F:\Ubuntu  with a 15 GB virtual HDD.

---

### Post by ago on 2008-10-31
It's

cat /proc/partitions

also try

mount -t ntfs /dev/sda1 /isodevice

---

### Post by Vertigo77 on 2008-10-31
Attached another photo. 
sda and sdb are 2 IDE drives which are used as a dynamic volume under XP.
sdc is the HDD where I am using wubi, and sdc6 coresponds to F: drive in XP.
I presume I should type mount -t /ntfs /dev/sdc6/isodevice . But I need to know what to type after it :) .

thanks for you help

---

### Post by ago on 2008-10-31
> **Vertigo77 said:**
> Attached another photo. 
sda and sdb are 2 IDE drives which are used as a dynamic volume under XP.


software raid arrays are not supported I am afraid.

---

### Post by ago on 2008-10-31
> **Vertigo77 said:**
> Attached another photo. 
sda and sdb are 2 IDE drives which are used as a dynamic volume under XP.


software raid arrays are not supported in 8.04 I am afraid. I haven't tested that with 8.10. They might work there but your luck may vary.

---

### Post by Vertigo77 on 2008-10-31
> **ago said:**
> software raid arrays are not supported in 8.04 I am afraid. I haven't tested that with 8.10. They might work there but your luck may vary.

The drive where I am installing Ubuntu is not part of the dynamic volume. I don't think the volume under XP has anything to do with this. Probably over the weekend I will physically disconect the 2 drives and see what's happening.

---

### Post by ago on 2008-10-31
I assume then you installed in sdc, which partition exactly?
Also note that in the command above there is a space missing. Use sdc1 instead of sda1

---

### Post by Vertigo77 on 2008-10-31
sdc6 is the partition that coresspond to the F: drive in windows

---

### Post by Cameron168 on 2008-12-14
Help im new to installing operating systems (ubuntu server edition). Can you help me it installed onto E: then it went fine looked like it was ready to go then it came up with this command prompt thing;

(initramfs) 

What do I do so it will go onto the server bit.

Thanks Cameron Marks

---

### Post by ago on 2008-12-15
> **Cameron168 said:**
> Help im new to installing operating systems (ubuntu server edition). Can you help me it installed onto E: then it went fine looked like it was ready to go then it came up with this command prompt thing;

(initramfs) 

What do I do so it will go onto the server bit.

Thanks Cameron Marks

Press esc at boot and try the other options, also see [https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

---

### Post by vanitor on 2008-12-17
hi, i can't load ubuntu 8.10, i install it fine with wubi, then i reboot, i try and click install ubuntu and my system just beeps once and then does nothing, no i move down and try and check for defects, also beeps, then i click boot from first drive, it loads up fine, i select ubuntu instead of windows xp it goes onto the splash screen for 2 seconds then dumps me onto the intramfs busybox page thing, it is installed on my c drive (same place as winxp) wich is a NTFS formatted drive, PLZ sum1 help.

---

### Post by ago on 2008-12-19
> **vanitor said:**
> hi, i can't load ubuntu 8.10, i install it fine with wubi, then i reboot, i try and click install ubuntu and my system just beeps once and then does nothing, no i move down and try and check for defects, also beeps, then i click boot from first drive, it loads up fine, i select ubuntu instead of windows xp it goes onto the splash screen for 2 seconds then dumps me onto the intramfs busybox page thing, it is installed on my c drive (same place as winxp) wich is a NTFS formatted drive, PLZ sum1 help.

It seems like you are using a live CD

---

### Post by PhilipKohn on 2008-12-22
I also got an (initramfs) prompt using 8.04 LTS amd64 CD.
Turning off the quiet option, I could see that it was getting lots of errors on the floppy disk (fd).
I tried the things mentioned in this thread and none of them worked for me.
What I did that worked was to put a floppy into the drive.
It still got fd errors, but this time it managed to get the cdrom driver loaded up before it dumped me into initramfs.
Everything was smooth from there.
Perhaps there is a race condition between checking devices and some sort of timeout that lands you in initramfs.
If that is true, it could be probabilistic, so it would be easy to think you found a work around when really it was just a lucky race.
(Maybe that my solution was also just luck.  I'd have to go and try it many times without changing anything to see for sure!)

---

### Post by HoradrimAncient on 2009-07-17
It's just 2 weeks since I started using Linux properly. :)

I first tried out with Ubuntu through a wubi install. worked perfect. now before I do a proper install I'm trying to try out Kubuntu as well. but this initramfs prompt keeps coming up. I tried everything else except "all_generic_ide" and "irqpoll" addition to the booting. will see how it goes. 

what i can't understand is how it works well with Ubuntu and not with Kubuntu.

update:
no luck with "all_generic_ide" or "irqpoll". i'm going to try reinstalling after a full NTFS reformat. but am not too hopeful.

---

### Post by HoradrimAncient on 2009-07-18
no use. i had ubuntu 9.04 installed via wubi and had 4 GB space set out for that. then to try kubuntu i uninstalled ubuntu and tried installing. everything went well until the restart when it returned this busybox + initramfs. tried to go back to ubuntu but that doesn't work now either. i don't know what has happened. :(

---

