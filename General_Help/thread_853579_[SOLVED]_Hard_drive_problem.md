---
title: "[SOLVED] Hard drive problem"
date: 2008-07-08
forum: General Help
---

### Post by RB2610 on 2008-07-08
I have 2 hard drives in my PC, both previously containing Windows XP, I recently installed Ubuntu over one of the XP installs but for some reason Ubuntu only seems to work properly if only the disk that it is running off of is connected, this is causing major problems because now I am unable to access any of the files in my larger (and newer) disk with the XP install.

When I try to boot into the old drive (the one with Ubuntu) with the new disk connected it starts to work but when it gets to the loading screen (the one with the orange bar scrolling along) it just keeps scrolling from side to side, I left it for a few minutes like this but it just continues to do that. This also happened when I was installing Ubuntu, it wouldn't get past the black screen when both hard disks were connected.

I would really appreciate help with this, it is very frustrating.

(If it is of any relevance the older HD (with Ubuntu) is PATA and the newer one (with XP) is SATA.)

---

### Post by VMC on 2008-07-08
> **RB2610 said:**
> I have 2 hard drives in my PC, both previously containing Windows XP, I recently installed Ubuntu over one of the XP installs but for some reason Ubuntu only seems to work properly if only the disk that it is running off of is connected, this is causing major problems because now I am unable to access any of the files in my larger (and newer) disk with the XP install.

When I try to boot into the old drive (the one with Ubuntu) with the new disk connected it starts to work but when it gets to the loading screen (the one with the orange bar scrolling along) it just keeps scrolling from side to side, I left it for a few minutes like this but it just continues to do that. This also happened when I was installing Ubuntu, it wouldn't get past the black screen when both hard disks were connected.

I would really appreciate help with this, it is very frustrating.

(If it is of any relevance the older HD (with Ubuntu) is PATA and the newer one (with XP) is SATA.)

> ...for some reason Ubuntu only seems to work properly if only the disk that it is running off of is connected Doesn't this sound obvious? I'm not sure I follow what your saying, but if you list out all your hard drive, maybe we can figure this out.

From a Terminal type the following messages:

```
sudos fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by RB2610 on 2008-07-08
I just tried the code you suggested, it said that sudos command is not found.

I have tried to explain as best as I can. when I tried to install (from a liveCD) it also wouldn't start with the new harddisk present. It came up with a message that kept repeating over and over again, I would write it but i cant get it to come up again without trying to install Ubuntu again.
I also had the same problem when I tried out Ubuntu using a Wubi install an few days ago, but that time it worked after I restarted a couple of times. But I have restarted several times with this and it doesn't work.

My Ubuntu HD has 4 partitions, /, /home, swap and /windows (a FAT32 partition just so i can transfer files). But I don't think this could be a problem as the problem was there before i had even finished (or even started) the installation.

---

### Post by RB2610 on 2008-07-09
*Bump*

I really need some help with this :(

---

### Post by plucky on 2008-07-09
> I just tried the code you suggested, it said that sudos command is not found.


The command is ```
sudo fdisk -l
``` that is lowercase L not a 1

I think you are having problems with drive names and numbers.Post the output of the commands **VMC** gave you so we can see your setup.

How do you boot into XP?
Do you use the Grub menu or your Bios?
When you installed Ubuntu,was your XP disk disconnected?
Do you need to disable your SATA drive to boot Ubuntu?
Can you boot XP with your Ubuntu drive connected?

The more information you give the easier it is for us to help you.

---

### Post by RB2610 on 2008-07-09
This is what came up:
> Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e3d2e3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    5  Extended
/dev/sda5           19526       20023     4000185   82  Linux swap / Solaris
/dev/sda6               1        1245    10000368   83  Linux
/dev/sda7           12055       19524    60002743+   b  W95 FAT32
/dev/sda8            1246       12054    86823261   83  Linux

Partition table entries are not in disk order

To boot into Windows I connect the new HD and change the boot order and it works fine.
I use the BIOS to change the boot order, I don't think a grub menu comes up.
No, I had to disconnect the XP disk for the installer to work, otherwise it just kept loading endlessly.
Yes, I need to disable the XP disk to boot into Ubuntu (by disconnecting it from the PC)
Yes, XP boots as usual when the Ubuntu drive is connected.

---

### Post by plucky on 2008-07-09
> I use the BIOS to change the boot order, I don't think a grub menu comes up.


How does the Bios see the two drives when they are connected?
Which is HD0 and which is HD1?
Also can you post the output of the second command ```
cat /boot/grub/menu.lst
```

I take it the Live CD won't boot when both drives are connected,which suggests to me that there is a conflict in drive naming and numbering.

How is your DVD/CD drive connected,is it SATA or PATA?
Is your PATA drive the Master and CD drive the Slave?
Are they on separate Ata connectors?

---

### Post by chrisccoulson on 2008-07-09
In addition to the information requested above, can you post the output of:
```
cat /etc/fstab
ls -l /dev/disk/by-uuid
```

---

### Post by RB2610 on 2008-07-09
Output for cat /boot/grub/menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f9a9bf38-73de-46fe-9efe-08d5ed7bfe10 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f9a9bf38-73de-46fe-9efe-08d5ed7bfe10 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f9a9bf38-73de-46fe-9efe-08d5ed7bfe10 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

The CD/DVD drive is SATA and I just checked and found that the PATA hard drive is set as Cable Select, I'll restart with it set as master and see if that works.

Output of cat /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f9a9bf38-73de-46fe-9efe-08d5ed7bfe10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=944fa6fd-05ae-4a87-8946-50a533eb3593 /home           ext3    relatime        0       2
# /dev/sda7
UUID=5EF0-109F  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=92fd9d5f-36ef-42d0-9ad7-c0680347d40a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks for the help so far :)

---

### Post by RB2610 on 2008-07-09
Ok, I switched the old HD from Cable Select to Master with those white bridge/jumper things (I forgot what they're called :s)
I booted up again, with both HDs present and it didn't work. So I restarted and pressed ESC when the option to enter the Grub menu came up, to see if Windows was listed, it wasn't so I just continued, then Ubuntu booted properly and the new Hard drive is present.
I'll reboot once more to check it continues to work, if so, problem solved :)

Thanks very much for your help, I don't know how to do the 'thank' option on this website, but i would if I knew how, I expect it is probably only an option when you are reading a post but for some reason i keep getting logged out of the site unless I'm posting, and to log in I have to delete my cookies and cache :mad:

---

### Post by RB2610 on 2008-07-09
After restarting the PC again I found that the problem is happening again, I seemed to get around it by fluke that time, at least I had a chance to get some of my files over to Ubuntu.
So I still need to solve this problem :( :confused:

---

### Post by RB2610 on 2008-07-09
*Bump*

Also I the Ubuntu HD is set as HD0 I think, but it might change when the other drive is added.

---

### Post by plucky on 2008-07-09
Can you boot the Live CD with both disks connected?

If you can,it would be useful to see the output of ```
sudo fdisk -l
``` That is lowercase L not a 1

You will not be able to boot windows from Grub as it was not present when Ubuntu was installed and has no entry in the menu.lst file.

Can you check in the Bios which drive is actually HD0 and which is HD1,as that is critical to how the system boots.

---

### Post by djbon2112 on 2008-07-09
Forgive me for pointing out the obvious, but could it simply be conflicting MBRs? Windows XP on one HDD didn't see a Windows MBR on the other, installed its own, and now both are conflicting?

---

### Post by RB2610 on 2008-07-09
I just tried booting into the LiveCD w/both HDs, it didn't work, a loading screen came up, then after that a message on a black screen came up mentioning 'Busybox' and then what looked like it's version number.
under this was a line saying: (initramfs), then something saying:
"[133.(a bunch of numbers)] ata3.01:revalidation failed (errno=-5)"
this came up about three times, each with slightly different numbers in the brackets.
Then another 3 lines, each preceeded by a load of numbers in brackets came up saying:
"[*numbers*] :exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen"
"[*numbers*] *this one consisted mainly of numbers, it started with 'cmd' though"
"[*numbers*] status:{DRDY}"

These 3 lines just came up repeatedly, every time with different numbers in the brackets, I left it for quite some time but it just continues to do it.

The only place i have seen any writing that mentions HDD0 is just after the boot screen, the old HD is listed with total space and HDD0 written next to it, this has always been like that, it only ever lists the old HD, so I assume the other one must be HDD1, unless that is what the problem is.

---

### Post by VMC on 2008-07-09
> **djbon2112 said:**
> Forgive me for pointing out the obvious, but could it simply be conflicting MBRs? Windows XP on one HDD didn't see a Windows MBR on the other, installed its own, and now both are conflicting?

That IS the problem. When you start manipulating drives using the BIOS, your asking for trouble. 

Ubuntu installed Grub and its stage1 into hd0 mbr. So I'm not sure who's hdo or hd1, since you moved things around both by the BIOS and sttaching one of the drives using the slave method.

---

### Post by RB2610 on 2008-07-09
> **VMC said:**
> That IS the problem. When you start manipulating drives using the BIOS, your asking for trouble. 

Ubuntu installed Grub and its stage1 into hd0 mbr. So I'm not sure who's hdo or hd1, since you moved things around both by the BIOS and sttaching one of the drives using the slave method.

All I have done to the hard drives in the BIOS is changing boot order, surely thats not likely to cause a problem.

---

### Post by RB2610 on 2008-07-11
After testing it a few times I have found that it still doesn't work consistently, I have to boot up between 3-6 times unless I'm very lucky.
I added Windows to the boot menu in Grub, but I was wondering whether maybe installing it in Windows as well might fix the problem, maybe if Windows is made to recognise the Ubuntu install there might not be problems? I dunno though. :confused:

---

### Post by RB2610 on 2008-07-14
*Bump*

---

### Post by RB2610 on 2008-07-19
*Bump* (again) I really need some help with this, I have tried changing everything I can but it still rarely works :(.

---

### Post by RB2610 on 2008-08-09
After giving up an this for some time I have been made to fix the problem due to other people in my family getting frustrated with having to use Ubuntu or getting me to swap over hard disks :roll:

I have however found a thread about a problem that seems to be vaguely similar: [http://ubuntuforums.org/showthread.php?t=220471]("http://ubuntuforums.org/showthread.php?t=220471")
The problem seems to be caused by having both an IDE and a SATA drive in use at the same time, however in my system the IDE drive is Ubuntu and SATA is XP.
After finding that whenever I use 'Recovery Mode' to boot it seems to correct whatever issue was previously happening and boots correctly, but obviously I can't just boot into recovery mode all the time. I have tried to change various settings in the Grub menu.1st file but they just make no difference or make things worse.
In desperation I even tried setting up the Windows boot loader to allow me to choose Ubuntu, but it doesn't work despite following the instructions ([http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/]("http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/"))
I also noticed that when I opened GParted to check how the drives are set up they are both labelled sda/sdb rather than one sda and one hda, as it should be.
I can't think of any other information that may be relevant at the moment, all I can think of is that the recovery mode corrects some incorrect label allocation or something, maybe there is a way to get Ubuntu to do that in a normal boot?

---

### Post by RB2610 on 2008-08-09
Oh, I tried the 'sudo fdisk -l' command with just the Ubuntu disk, and then with both disks when I booted in recovery mode.

With just the Ubuntu disk the output was something like this:
"   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    5  Extended
/dev/sda5           19526       20023     4000185   82  Linux swap / Solaris
/dev/sda6               1        1245    10000368   83  Linux
/dev/sda7           12055       19524    60002743+   b  W95 FAT32
/dev/sda8            1246       12054    86823261   83  Linux"

With both disks in recovery mode I got:

"Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda42da42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e3d2e3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20023   160834716    5  Extended
/dev/sdb5           19526       20023     4000185   82  Linux swap / Solaris
/dev/sdb6               1        1245    10000368   83  Linux
/dev/sdb7           12055       19524    60002743+   b  W95 FAT32
/dev/sdb8            1246       12054    86823261   83  Linux"

Note that with both disks present Linux has been labelled sdb rather than sda (Although I think it should be hda) Which also happens in GParted.

---

### Post by RB2610 on 2008-08-09
*bump*

---

### Post by Victormd on 2008-08-09
Just a thought, but have you tried using [supergrub]("http://www.supergrubdisk.org/") to fix this problem? Connect all your HDs and boot using the supergrub live CD and go from there...

---

### Post by RB2610 on 2008-08-09
Thanks, I'll try that :)

EDIT: Yay, I've found out how to use the thanks thingy :D

---

### Post by Victormd on 2008-08-09
Let us know how this works...

---

### Post by RB2610 on 2008-08-09
Yeah, I think I need to go and buy another CD-RW, the only one I can find has the Ubuntu .iso on it :roll:

---

### Post by Bucky Ball on 2008-08-09
Like Victormd said. Try booting from supergrubdisk with all hard drives in and *without* the cd in. Let us know. 

Just out of curiousity, which OS did you install first? Windows plays some funny tricks when it comes to being first in line for drive allocations and will try to put itself as hda0 *always* in its MBR. Therefore, Windoze goes in first so it can be where it likes it ... no. 1; Linux next. This could be a clue, maybe not ...

It could be why your Ubuntu is sda1 etc but when both disks are in, it become *sdb1 etc* ... ! The grub wouldn't have a clue if Windows is pushing Ubuntu ID up one. Grub finding wrong thing in the place Ubuntu is supposed to be.

Typical dual boot install?

Both drives in. Windows on IDE drive. Ubuntu next on SATA. Hardy 8.04 usually can sort out the grub without hassle. If not, supergrubdisk and I just about guarantee you will be dual booting in next to no time (or a hour or two in any case).

Good luck with it all ...

ps: I am by no means saying this is the only or 'right' way to go. Just simple and will get you up and running for the moment until you learn how to tweak your grub some more.

My personal preference is to dual boot from the first two partitions on the same drive. My desktop has 4 drives and I still do this. Reasons? I keep all of my important 'dynamic' data (eg personal data) off the OS partitions altogether (usually on another drive altogether). If an OS crashes I just kill the partition and reinstall, nothing is lost. It also makes it easier (for me) to troubleshoot things like your problem because I'm only dealing with one drive and sda1=Windoze; sda? = Ubuntu and sda? = Ubuntu swap. You can then put /home on sda? or *sdb?*, another partition or drive (or up with one of the many permutations possible you might desire). Once the two ops are there, you can design how you want to go. Paper and pen is good before setting of on your partitioning journey. :)

---

### Post by RB2610 on 2008-08-09
Windows was installed 1st, but I would like to keep Windows on the SATA drive as it has much more space which I need for the wider range of games I have installed on it (although I do have several on Ubuntu)

What do you mean by 'without the CD in'?

(I went out and bought a bunch of DVD-RW disks, it was all the shop had, little did I realise for burning .iso's it has to be a CD-RW, luckily I found a CD-RW that had Nero or something on it so I just stuck that on a DVD so I can use the CD for this :) )

---

### Post by Bucky Ball on 2008-08-09
DVD fine for iso. UbuntuStudio installer for instance is over a gig so doesn't fit on cd, you have to use DVD. :)

> What do you mean by 'without the CD in'?

Make sure you have both drives in (windoze on one and Ubuntu on the other) and the cd tray is empty. Then you know you are looking at just those two drives and nothing else (no boot or any other cds). Boot up but go to Setup (bios), set to boot from cd, insert your supergrubdisk then save changes and exit (f10 probably). supergrub will do the rest. If it doesn't find two operating systems and set them up, back to the drawing board.

It is odd that Windoze was on first. Presuming you are using Hardy - it usually sets up grub for you (where as older version eg Gutsy, didn't necessarily).

Good luck

---

### Post by RB2610 on 2008-08-09
Oh, Nero didn't seem to like it :confused: oh well its on a CD now.

---

### Post by RB2610 on 2008-08-09
I booted the Super Grub Disk and I was overwhelmed by all the options :( I didn't want to do anything that could cause further problems so the only thing I did was went on view partitions which showed some interesting results, it showed the IDE Ubuntu disk as hd0, the Windows SATA disk as hd1 and then the Ubuntu disk again as hd2, I'm tempted to just change the Grub options in Ubuntu to use hd2 instead of hd0 to see what happens (if it doesn't work I can just boot in recovery mode and change it back)

---

### Post by Bucky Ball on 2008-08-09
That is worth trying ... Look before you leap!

[http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

SuperGrub is a teaching tool also ... if you explore the options in there it will fix it (98% chance!). It can see your installs so you are a step a way I would imagine. Got to go to bed now but there is another page somewhere that explains supergrub with a walk through if you can find it ...

I'll check back later today ...

---

### Post by RB2610 on 2008-08-09
Thanks for the help :)

---

### Post by RB2610 on 2008-08-09
UPDATE: Wow, after reading another thread about someone who's Ubuntu kept hanging on startup I deccided to try deleting 'quiet splash' from the boot to try and narrow down what the problem is, I was expecting it to have issues with a hard disk or something but I found that it was actually a driver for a USB mouse that it couldn't find or something, so I removed the mouse, rebooted and lo and behold, it works!!

Now I just need to figure out why the presence of a SATA HD is causing my USB mouse to mess up the start up process, it has never done it without the Windows disk so why is it a problem with it? :confused:

---

### Post by Bucky Ball on 2008-08-09
Have you added the 'quiet splash' command permanently, or are you having to apply the fix each time?

You can go to;

```
sudo gedit /boot/grub/menu.lst
```... and find the boot that you are changing each time. It will be down near the bottom. For now, just add *exactly* what you are adding at boot each time. For now, don't change anything apart from that, you can screw things up but don't panic, if it is working at boot this is what you are doing for each session to the file anyhow so it will work fine permanently.

Save file, reboot and now it will boot fine each time and you can concentrate on the SATA HD/USB conundrum.

Great news you are getting somewhere; why didn't I think of that? lol. These pages explain what is going on and you will probably get further when you know what 'quiet' and 'splash' actually to;

[http://www.linux.com/feature/62434](http://www.linux.com/feature/62434)

and ... 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

;)

---

### Post by RB2610 on 2008-08-10
I had permanently added it in the menu.1st file.

This morning I tried booting without the mouse and it instead hung at a different point, after a line that mentioned a SATA drive (could have been DVD-RW drive or HD) there was a line that said something to do with a bridge and it hangs there, although in both cases (the mouse driver issue and this one) after a while it kept trying to locate a driver or something, it continously does this, I can leave it for quite some time and nothing changes.
I tried rebooting several times w/ and w/out the mouse and except on a few occasions after removing the mouse, it alwyas ran into one of these problems, I have booted in recovery mode again to post this, I'll get some better info from the boot text and then post what I can.

---

### Post by RB2610 on 2008-08-11
The 'bridge' message said 'Applying Bridge Limits' this is where it hangs when the mouse is not connected.

---

### Post by RB2610 on 2008-08-11
*Bump*

---

### Post by Bucky Ball on 2008-08-11
[FONT=monospace]The following fixes a problem that sounds identical to yours. Try;

[/FONT]> [FONT=monospace]Add irqpoll to the kernel boot options. When booting, in grub, hit 'e' to edit the boot entry, then hit 'e' to edit the image line, and add irqpoll to the end of the line, hit enter, then 'b' to boot.
[/FONT][FONT=monospace]... (they mean add 'irqpoll' at the end of the line that starts with 'kernel') from this page;

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29006](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29006)

It might fix your problem. They give the error message as;

[/FONT][FONT=monospace]>  [4294797.380000] irq 201: nobody cared (try booting with the "irqpoll" option)[/FONT]
[FONT=monospace] 
Read the page for details. Even though the page refers to older kernel, still applicable. If you don't know how to do the fix with editing the grub menu at boot, let me know. :)

[/FONT]

---

### Post by RB2610 on 2008-08-11
Would it work adding it to the boot.1st instead?

---

### Post by Bucky Ball on 2008-08-11
Edit the grub way *first* before you add it permanently. You want to check it is going to work.

Extremely unlikely, but if it fails to boot from this command, you can just soft boot button on the machine and it will have dropped your changes and boot as normal. If you do it permanently before you know it is going to work, it could become a little nightmare-ish if things go pear shaped. :)

---

### Post by RB2610 on 2008-08-11
It seems to fix the mouse problem but it instead hangs on 'Allpying Bridge Limits', which comes up after a line mentioning the disk drive, I'll see what happens with the irqpoll command and the disk drive unlpugged.

---

### Post by Bucky Ball on 2008-08-11
It fixed the mouse problem??? Cool. You should leave the drive plugged in now and tell me what error it throws if you know for sure the mouse is fixed. Then we know it is the drive. Could you say exactly what? Recovery boot may give you a bit more detail (possibly even fix). Good luck.

(BTW, if it fixed the mouse problem, apply it permanently).  :)

---

### Post by Bucky Ball on 2008-08-11
Is there any other USB device plugged into the machine and switched on apart from the mouse? Printer, scanner, handset?

---

### Post by RB2610 on 2008-08-11
Ok, I restarted succesfully 3 consecutive times, so it seems that the irqpoll command fixed the other problem as well somehow. So it seems the problem is fixed, but I'll post back again if it happens again in the next few days.

Just out of intrest, what does the irqpoll command do?

EDIT: at the moment there are no other devices plugged in, although I have a 360 control pad that I usually have plugged in.

EDIT2: I rebooted with the control pad and everything is still fine :)

---

### Post by Bucky Ball on 2008-08-11
Love it when a plan comes together! ;)

That is good news. Should work permanently now after your grub edit in terminal.

> The option irqpoll, just basially polls the devices and get the right irq. If you don’t put this option it will basically hang at some point. From this site;

[http://www.csse.uwa.edu.au/~ashley/fedora-ds/fc6-intel965.htm]("http://www.csse.uwa.edu.au/%7Eashley/fedora-ds/fc6-intel965.htm")

It is to do with interrupt requests, where things are trying to communicate at boot (or not!). Your situation was probably the latter! Sure there is more info about. 

I'll consider this thread solved for now?

Good luck with it all ... :)

---

### Post by RB2610 on 2008-08-11
Thanks :)

---

### Post by RB2610 on 2008-08-11
I can't delete messages :s (I don't need this one)

---

