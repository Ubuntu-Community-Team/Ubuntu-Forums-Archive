---
title: "I think I messed up installing Edgy. Please help!"
date: 2007-01-31
forum: General Help
---

### Post by Roasted on 2007-01-31
I thought I was doing everything right but somehow I goofed up.

I'm working with 3 hard drives, however I'm only changing the OS on one hard drive.

My main SATA drive has a 30 gb partition of Windows 2000 Pro on it, and I have a 512mb linux-swap partition, along with the remainder (203 gig) being primary partition ext3. The 512mb swap partition is mounted to swap, while the ext3 partition is mounted to root.

When I installed Edgy the first time from a live cd, I rebooted after it was done and I got an error with grub. I forget what the error said, but I got error 22 I believe. I tried to boot into windows and I got error 14 I believe. The reason I say "I believe" is I'm unsure of which OS got which error, but I DO remember 14 and 22 (pretty sure).

Anyway, I tried installing it again. So I go through, step by step, and I'm unsure WHAT could of happened. At the last screen before I hit "install" I saw a bubble in the list, saying where GRUB was written to. I believe it said HDA. I thought, hm, maybe GRUB should be on SDA (which is my main drive with the windows/linux swap/ext3 partitions). Well, I got a "fatal error" at the end of the installation.

I'm lost. I'm on the live cd now just running firefox and hoping someone I know that's good with linux can pop online. But at 12:30 AM I'm not sure! Please help. :(

---

### Post by logos34 on 2007-01-31
what does 
> sudo fdisk -l 

show?

---

### Post by Roasted on 2007-01-31
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        3889      522112+  82  Linux swap / Solaris
/dev/sda3            3890       30515   213873345   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   5  Extended
/dev/sdb2              63       30515   244613722+  83  Linux
/dev/sdb5               1          62      497952   82  Linux swap / Solaris

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       24792   199141708+  83  Linux
ubuntu@ubuntu:~$

---

### Post by logos34 on 2007-01-31
What's on hdd1?  

I'm thinking maybe grub went to the mbr on ide drive hdd (primary master?)...In your bios verify that the boot order is your main sata drive (sda) first, then hdd, then optical...Could be your grub menu.lst is got messed up as result and needs editing...Or maybe fstab has the wrong entries

---

### Post by Roasted on 2007-01-31
hdd1 has nothing except my home folder. Same with sdb2.

Considering the fact I have about 4,000 pictures that I refuse to let go of (plus about 7,000 songs and a ton of school files and full text books in pdf format) I backed up my home folder twice. 

SDB2 (sata) and HDD1 (ide) are both hard drives with no operating system. They are both formatted with EXT3 and have my home folder on them as backup. SDA is the drive I am using for my primary.

How can I get the grub boot loader to load on the proper drive? And, quite frankly, where is the proper location for it to be written to? 

On SDA I have a 30 gig windows partition, 512 mb linux swap, and 203 gb ext3 primary partition. Where should the MBR go? And how can I even re-install it?

---

### Post by logos34 on 2007-01-31
you can try to restore grub.

Do this:

In a terminal type  
Type 'sudo grub'
then at the grub>, type 'find root (hd' and hit the Tab key after the 'd'--it will show autocomplete for you, then hit it again and a list of partitions will show up.  Then you can use that to setup grub again.

---

### Post by Roasted on 2007-01-31
After I type sudo grub, everything disappears and this is all I see.



       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 






I've about had enough. I'm about to reinstall windows too and do a fresh install for the entire hard drive. But there's no reason to do that, I'm just so aggrivated with it.

How can I flat out reinstall grub? I know there's a way, but why can't I figure it out?

---

### Post by logos34 on 2007-01-31
sorry for the delay...it appears i'm having dsl connection problems...had to reset modem...just a sec

---

### Post by logos34 on 2007-01-31
ok, you have the grub prompt (grub>), so just type 'find root (hd' and hit the Tab key after the 'd'--it will show autocomplete for you, then hit it again and a list of partitions will show up. sda is probably 'hd0'.  but this will verify

---

### Post by Roasted on 2007-01-31
I just sat here and typed in about 40 different things. I assume you meant to just type in "find root" and I did. No luck. I tried a ton of other things cause I wasn't completely sure what you were looking for.

This is all I get with find root.




grub> find root

Error 15: File not found

grub> 





What EXACTLY should I type?

---

### Post by logos34 on 2007-01-31
grub> **find root (hd**

hit the tab after d, and then again.

---

### Post by Roasted on 2007-01-31
grub> find root (hd
 Possible disks are:  hd0 hd1 hd2

grub> find root (hd
 Possible disks are:  hd0 hd1 hd2

grub> find root (hd

---

### Post by logos34 on 2007-01-31
now, put **0** after the d and hit tab

---

### Post by Roasted on 2007-01-31
It inserts a comma.

grub> find root (hd0,

---

### Post by logos34 on 2007-01-31
hit tab again... a list of partitions should appear (probably sda1-3)

---

### Post by Roasted on 2007-01-31
I just hit tab about 19 times.

All I got was this.


grub> find root (hd0,0)

---

### Post by logos34 on 2007-01-31
we were looking for something like this (here's mine)

> grub> find root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83

Why don't we just assume hd0 is /dev/sda and do a quit setup of grub there.  so your root is on sda3, which grub will see as hd0,2

Do this:

Type 

grub> root (hd0,2) 

grub> setup (hd0)

Quit grub by typing "quit". 

Reboot.

---

### Post by Roasted on 2007-01-31
Hm... Here's what I found. Even though I got the errors, I kept going ahead to see if anything would happen.





grub> root (hd0,2)     

Error 22: No such partition

grub> setup (hd0)

Error 12: Invalid device requested

grub>

---

### Post by logos34 on 2007-01-31
oh, make sure to change the bios to boot from main sata.  If you can't boot into either os, boot back into the livecd, come back and we'll open up and edit menu.lst and fstab.

---

### Post by Roasted on 2007-01-31
My HDD boot disk priority is set right.

SATA 1
SATA 2
Maxtor IDE

Now what?

---

### Post by logos34 on 2007-01-31
we have to get into your menu.lst and fstab files, to do that we have to mount sda3 

grub> quit

get back to regular prompt.

then, enter these commands in one after the next

sudo mkdir /ubuntu
sudo mount -t auto /dev/sda3 /ubuntu
cat /ubuntu/boot/grub/menu.lst

copy and post menu.lst

---

### Post by Roasted on 2007-01-31
ubuntu@ubuntu:~$ sudo mkdir /ubuntu
ubuntu@ubuntu:~$ sudo mount -t auto /dev/sda3 /ubuntu
ubuntu@ubuntu:~$ cat /ubuntu/boot/grub/menu.lst
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
# kopt=root=UUID=04bd224e-be7f-4591-8042-6bd420c0d345 ro
# kopt_2_6=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows 2000 Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

ubuntu@ubuntu:~$

---

### Post by logos34 on 2007-01-31
see, sda is hd1, not hd0 (although you would think it would be since your main sata is first in boot sequence..

Real quick, before you do setup on hd1, post output from 
cat /ubuntu/boot/grub/device.map
cat /ubuntu/etc/fstab

---

### Post by Roasted on 2007-01-31
ubuntu@ubuntu:~$ cat /ubuntu/boot/grub/device.map
(hd0)   /dev/hdd
(hd1)   /dev/sda
(hd2)   /dev/sdb
ubuntu@ubuntu:~$ cat /ubuntu/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=04bd224e-be7f-4591-8042-6bd420c0d345 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
UUID=c5c11e0c-1ae9-4709-823b-e87fd4dc5d7a /media/hdd1     ext3    defaults        0       2
# /dev/sda1
UUID=3AFC77ECFC77A0B5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=a4795e73-acf5-4b59-bb3f-4b8086f8619b /media/sdb2     ext3    defaults        0       2
# /dev/sda2
UUID=ba6881e1-1e53-4410-9782-b3d4c1f61755 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
ubuntu@ubuntu:~$ 








Also - Note, I have no idea which drive is first in boot sequence. sda and sdb are both 100% identicle hard disk drives. But I haven't touched those bios settings, and sda WAS set first.

Can't I just alter it to be hd1 instead of hd0? If so, how would I do that? I'm kind of drifting off into sleep... so if I don't get an answer too soon I'll be sure to check back here first thing in the morning. If that's the case, then I'd like to thank you now for your help!! :)

---

### Post by logos34 on 2007-01-31
well, everything looks in order in both....

yes, just substitute hd1 for hd0...Can't promise you it will solve anything because everything looks ok...the problem is elsewhere I think

first unmount sda3:
> 
sudo umount /dev/sda3

get back to grub prompt
> sudo grub


then

> root (hd1,2)
setup (hd1)
Quit grub by typing "quit".
Reboot.

---

### Post by logos34 on 2007-01-31
while you're doing that, here's the official definition of the error messages your were getting:

# 14 : "Filesystem compatibility error, can\'t read whole file"

Some of the filesystem reading code in GRUB has limits on the length of the files it can read. This error is returned when the user runs into such a limit.



# 22 : "Must load Multiboot kernel before modules"

This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.

---

### Post by rajan on 2007-01-31
Logos,
 do i need to change the menu.lst file if i can't get my old HD to mount? TIA...

---

### Post by logos34 on 2007-01-31
> do i need to change the menu.lst file if i can't get my old HD to mount?

possibly, if you're trying to boot from it...Or do you just want to mount the partitions to access the files on it?

---

### Post by rajan on 2007-01-31
> **logos34 said:**
> possibly, if you're trying to boot from it...Or do you just want to mount the partitions to access the files on it?

ya... i'm just trying to access the files from it. i think i could just use a tutorial of how to mount a HD from the live CD because i'm having a lot of problems with that. if you know where one of those is on this site, i'd really appreciate it. sorry to hijack the thread.

---

### Post by Roasted on 2007-01-31
That didn't work when I did that. Nothing happened. I switched the boot order in BIOS, switching the other drive to be first, and it hung at "boot from disc." I don't know about you guys, but a second before grub starts it says boot from disc twice in a row, then grub 1.5 loading, and my OS's come up. It just hangs at boot from disc when I switch them. 

I'm going to give this topic another 10-15 minutes, if I get no responses I'm going to just format the drive and redo everything, including the windows partition too.

---

### Post by logos34 on 2007-01-31
I waited for you earlier this morning...i guess you were just too tired and nodded off...sorry I couldn't get back to you sooner...

If you haven't already gone ahead and reinstalled, then do it because it'll probably be quicker than troubleshooting...Remember, windows goes in first, so grub will overwrite win bootloader and not the other way round...when you get to the 'ready to install screen' with the 'bubble' showing where grub will be installed, make sure to choose the right disk (it'll say '(hd0)' or '(hd1)', etc...I can't figure out what happened the first time you installed because you see grub menu when you boot to sda, so it obviously installed to the mbr of of that disk, but when I had you do that 'grub> find root (hd' routine it came back 'root (hd0,0)'--which is hdd1.  I thought doing a setup would be something to try first...sometimes it works. 

You might want to download the text-based alternate install cd and use that instead of the livecd...gives you more control over the installation process.

Add: You can also unplug your other drives to be absolutely sure that everything goes on your main sata...but that means you'll have to add entries manually for the other drives to fstab.

---

### Post by Roasted on 2007-01-31
You're telling me that my MBR was written to hdd1? Are you sure of that?

If that's the case, that makes sense. hdd1 is just an IDE drive I have that has no operating system and has a backup of my home folder from my previous install.

---

### Post by logos34 on 2007-01-31
> **rajan said:**
> ya... i'm just trying to access the files from it. i think i could just use a tutorial of how to mount a HD from the live CD because i'm having a lot of problems with that. if you know where one of those is on this site, i'd really appreciate it. sorry to hijack the thread.

Check out [this link]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") and the mount windows and linux links [here]("http://www.psychocats.net/ubuntu/index.php").  Start a new thread if you;re still having probelms.

---

### Post by logos34 on 2007-01-31
> **Roasted said:**
> You're telling me that my MBR was written to hdd1? Are you sure of that?

If that's the case, that makes sense. hdd1 is just an IDE drive I have that has no operating system and has a backup of my home folder from my previous install.

no, that's where 'find' was saying your root (with /boot) partition was...something's screwy somewhere...if you notice in fdisk there;s a '*' in the 'boot' column before hdd1...if it's not too much trouble a reinstall might be your best bet

---

### Post by Roasted on 2007-01-31
I already did reinstall. Everything. I unplugged hdd1 and sdb2 (backup drives) and ran sda1 solo. Installed windows and edgy. Everything is fine now. All drives are back in, my home folder has already been copied over to edgy's fresh install, now all I'm doing is running automatix and automatix 2 to get the latest... well, everything I need.

The only aggrivating issue I'm having at the moment is I cannot get gaim to work. It just won't connect, and I don't know why. I'm positive of my screen name and password. I just don't get it.

---

### Post by logos34 on 2007-01-31
> **Roasted said:**
> I already did reinstall. Everything. I unplugged hdd1 and sdb2 (backup drives) and ran sda1 solo. Installed windows and edgy. Everything is fine now. All drives are back in, my home folder has already been copied over to edgy's fresh install, now all I'm doing is running automatix and automatix 2 to get the latest... well, everything I need.

The only aggrivating issue I'm having at the moment is I cannot get gaim to work. It just won't connect, and I don't know why. I'm positive of my screen name and password. I just don't get it.

ok, great.  So you used the livecd and everything works?  Did you edit your fstab so you can mount and access your other disks?

---

### Post by Roasted on 2007-01-31
I used the livecd to install, yes.

What I did was I just put the windows cd in and installed that first. After that was all done, I threw in the livecd and installed linux, 512mb swap and 208gig ext3 primary.

I was able to mount the drives manually once the OS booted and copied the files back over to my main drive.

The only thing is, my windows partition auto-mounts whenever I boot. How can I edit that?

And for the love of small healthy children, how can I get gaim to work? My router has port 5190 forwarded. So why is gaim suddenly deciding it won't let me connect?

Also, it's been a while... with the repos that are installed, should I just hit each one and enable universe/multiverse on all of them?

---

### Post by logos34 on 2007-01-31
> The only thing is, my windows partition auto-mounts whenever I boot. How can I edit that?

what, you don't want it to automount?  Why not?  You can just change the options in fstab...Post it if you could.

> 
Also, it's been a while... with the repos that are installed, should I just hit each one and enable universe/multiverse on all of them?

I have all mine enabled (universe, main, multiverse, restricted and source code)

Can't help on gaim.

---

### Post by Roasted on 2007-01-31
This looks incredibly different than dapper. How can I enable ALL of my repositories? I'm going to them through synaptic. The menu at this point just looks different. 





As far as the fstab thing, how can I get into it? And why would I want my windows partition to mount? It ONLY contains games. I have no reason to use windows unless I'm playing a game.

---

### Post by logos34 on 2007-01-31
> How can I enable ALL of my repositories? 

Settings>Repos>software sources>Ubuntu 6.10 tab

Well, if it's just games, then i guess there is no reason to have access to windows parititon from within linux.

Fstab:
> gksudo gedit /etc/fstab

---

### Post by Roasted on 2007-01-31
I'm using automatix 2, and as I watch everything install I'm getting a TRUCKLOAD of "couldn't find packages". Is this because all of my repos aren't enabled?

edit - Everything under the ubuntu 6.10 tab is checked. I guess everything is enabled? What's with the automatix 2 thing then?

---

### Post by Roasted on 2007-01-31
Things just get better and better. 

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-2.png[/IMG]

---

### Post by logos34 on 2007-01-31
Did you hit 'reload' button after adding repos? And in the Internet Updates tab in Software Sources you should have 'Important security' and 'recommended' updates ticked...Maybe try reboot...dunno

---

### Post by Roasted on 2007-01-31
I didn't do ANYTHING. They were installed all checked. That's why I'm confused.

This seriously has me contemplating on going back to Windows. There's no reason for GAIM to not work. The port is forwarded. The password is right. Yet Edgy says nope, we're not connecting. Why won't GAIM work?!?!

I'll reboot and try automatix 2. If this doesn't work, I'll be spending the evening in win2kpro. I really REALLY don't want that... So if anybody has any ideas that can help, feel free to share!!!!

---

### Post by Roasted on 2007-01-31
I reset my router and I'm on aim now.

But why would that fix aim if I was already online downloading, on yahoo messenger, etc? And why did it suddenly block all 4 computers??

---

