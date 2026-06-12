---
title: "RAID insanity: &quot;md: array md1 already has disks!&quot;"
date: 2007-05-29
forum: General Help
---

### Post by Havlock on 2007-05-29
Got a nasty suprise when I came back from Memorial Day vacation; my Ubuntu 7.04 server would no longer boot up. It wasn't able to get the two Linux RAID1 arrays that make up my root assembled. The first two times I started the system, it'd get to either "stopping md0" or "stopping md1", sit around for a long time, then drop out to initramfs (I think it's called that.) And after that it would do the same thing, but now it's spamming "md: array md1 already has disks!" to the console, making it impossible to use the initramfs command line.

What I'd like to know is how to get my Linux RAID back in order and booting up. I do have Internet access from a system on the same network that my server is on, so getting any needed tools won't be a problem. I really want to get this server working again, since it does quite a bit for me.

---

### Post by Havlock on 2007-05-29
Justa bump to keep it on the front page.

---

### Post by Havlock on 2007-05-29
A bump and a bit more info:

Before, when I'd shut down the server using the poweroff command, it would go through the regular notifications of the various processes and systems it was stopping. Every time, since I've had the Linux RAID, it would give a big red "FAIL" when the server tried to stop md0 and md1. It wouldn't hang or anything like that, and until this current problem it didn't cause trouble. Just another tidbit of information that may or may not help.

---

### Post by Havlock on 2007-05-30
Bump!

---

### Post by apalsola on 2007-06-06
Hello!

I had a similar problem this morning on a 64-bit Kubuntu 7.04 (Feisty) with all upgrades installed.

I booted in rescue mode from the Alternate boot CD and let it find the md array. (I didn't have to mount the arrays nor to run any specific commands.) Then I rebooted from the hard disks and the system booted up OK, but the md1 array was degraded. It is rebuilding the array now and everything seems to work OK.

I don't know what caused the problem initially or what actually solved it. The problem just seems to be away, at least for now. I hope it won't repeat itself.

You might want to check out this, too: [http://ubuntuforums.org/showthread.php?t=435281]("http://ubuntuforums.org/showthread.php?t=435281")

HTH!

---

### Post by Midahed on 2007-08-17
I've just had the same problem.

System is Ubuntu 7.04 Feisty 64-bit workstation with both partitions (root and swap) set-up as raid1.  It's been working fine for a month or so, but on this morning's boot-up I got the 'md: array md0 already has disks!' message scrolling up the screen.  Like someone else having the same sort of issues in a different thread, I have break=mount set in my menu.lst to get round the array assembly race condition bug, and the break hadn't been reached, so it looks like this happens during array assembly before the device is mounted.

I booted into SystemRescueCD and ran fdisk -l.  This showed that hdc (the second drive in the raid pair) had no partition table.  Loading gparted just gave the same result - an apparently blank un-partitioned drive.  I then ran gpart, but it's drive analysis (which took hours to complete) effectively said there was nothing on the disk!  All four primary partitions were reported as being zero cylinders in length.

I then switched off the system and spent some time moving backups off my usb drive to clear space prior to backing up the working drive (hda) before starting any recovery work.

I again rebooted the system using SystemRescueCD and ran fdisk -l just to check a few things on the layout of the working drive... and found that hdc looked OK!

I took the SystemRescueCD out, booted the system normally and up it came - with both arrays in place.  Using cat /proc/mdstat and mdadm --detail both showed that the arrays were running and clean.

The odd thing is that I didn't do anything to fix the problem - it just seemed to disappear.

Anyone else seen partition information disappear and then come back by itself?

Mike

---

### Post by Midahed on 2007-08-17
OK, here's a bit more info....

It's happened again - several times - and a pattern seems to be emerging. 

The system boots OK most of the time, but occasionally falls over with the "md: array md0 already has disks!" error as described in my previous post.  However, what appears to be happening is that once the error arises, the system will continue to fall over in the same way until the PC is powered-off.  Once it's been powered-off, there's a very good chance (>90%) that the next boot will be fine.  To support this point, I waited until the system failed and then re-booted without a power-cycle about fifteen times.  On every occasion, the system failed to boot up.  I then power-cycled the box and the next boot worked,  I repeated the whole test three or four times.

After sitting here doing around 60 reboots, I can say it's a darn good job it does it a lot faster than one of Bill Gates' offerings :)

Each time this happens the underlying cause is that drive hdc has lost it's partition table but, having been powered down, the partition table is OK on the next boot and everything works.

Because of the effect of a power-cycle over a soft restart, my nose is pointing me towards a hardware-ish problem here, rather than flaky software.

Anyone got any views?  I've seen some odd hardware problems in my time, but this intermittent loss of the partition table that's fixed by a power-cycle, but not a reset, is a bit extreme....  You'll see from my last post that gparted and fdisk -l both confirm that there's no partition information, so it's not a problem that's confined to something like the kernel modules loaded by initrd during the boot process - hence my feeling that it's more likely to be hardware-related. 

On the other hand, a hardware problem is OK.  I can live with that - it just helps my self-justification for a nice new pair of big fat SATA drives :)

Any views, anyone?

Mike

---

### Post by klausbreuer on 2007-09-06
*sigh*

Exact same error here today, after the latest update yesterday evening, Sep. 5th 2007 (Feisty 7.04). I had updated Ubunto to the latest version, had to do a reboot and instead simply powered the system down.

Initially, I thought it might be a hardware failure - drive #6 on my RAID-5 array refused to start up at times in BIOS. If I repower the system, sometimes it'll come up after all, and the array works fine.
I'll replace this, so okay, but...  today dmesg shows a different drive failing:

[   32.667850] md: md0 stopped.
[   32.775643] md: bind<sde>
[   32.775793] md: bind<sdf>
[   32.775930] md: bind<sdg>
[   32.776067] md: bind<sdh>
[   32.776236] md: bind<sdd>
[   32.776403] md: bind<sdc>
[   32.776539] md: bind<sda>
[   32.778534] md: array md0 already has disks!
[   32.779910] md: array md0 already has disks!
[   32.781284] md: array md0 already has disks!

And as you said, the whining 'array md0 already has disks!' keeps coming up after this.

The only bind missing is for <sdb>, which has been running fine for a while. As did <sda>, just in case the error triggers before the bind of <sdb>.

Now this is an additional array, so I can boot the system up... but I'd really like to see my system work properly! :confused:

Any help would be much appreciated!

Ciao,
Klaus

---

### Post by fjgaude on 2007-09-06
Is anyone using UUIDs instead of the /dev/sd[a,b,c]s?

frank

---

### Post by Midahed on 2007-09-07
I'm not using UUIDs in /etc/fstab or in /boot/grub/menu.lst, but elsewhere, yes.

Why do you ask?

Mike

---

### Post by fjgaude on 2007-09-07
From my limited experience Linux seems to randomly change which drive gets which sda, sdb, etc. Using UUID in fstab seems to solve this switching around, especially when it comes to assembling raid arrays automatically the way mdadm does.

I have determined the UUID for each drive and array and only use them and not the sda1, sdb1, etc., in fstab and menu.lst.

frank

---

### Post by spirilis on 2007-09-25
I just noticed this start up on my server.  It's been working fine until yesterday I booted it up (haven't migrated everything to it completely so I power it down in the evenings) and noticed later on, the server had no ping (even though it was powered on).  Console was unresponsive.

Power cycled the box, and I got that "array md0 already has disks!" which scrolls ad infinitum during bootup, and never gets past that point.  I booted the Ubuntu 7.04 server CD in rescue mode and it loaded the array correctly, then I rebooted and the system booted up normally on its own.  Shut it down for the evening.
Then this morning, I tried booting it up, and was greeted with the "array md0 already has disks!" scrolling ad infinitum, and didn't get past it.


My setup involves a small RAID1 (/dev/md0) between two 500GB SATA disks which houses the root filesystem, including /boot.  Grub sets root=/dev/md0 during bootup.
The rest of the O/S is held on /dev/md1, which is a RAID1 comprising the rest of the disk.  (/dev/md1 is managed by LVM, but /dev/md0 isn't)

All underlying partitions are set 'Linux raid autodetect' on the disks.

---

### Post by fjgaude on 2007-09-25
Let us see what your /boot/grub/menu.lst file looks like (just the bottom part that shows the grub menu items, as well as your /etc/fstab.

sudo gedit /boot/grub.menu.lst
sudo gedit /etc/fstab

That should do it. Copy and paste them into a message here.

I think you need to be mounting only UUIDs for the drvice, drive nomenclature.

---

### Post by spirilis on 2007-09-25
Huh, so can I use the UUID for /dev/md0 as you see when you do "mdadm -D /dev/md0"?
Right now it does it once when I reboot, then I hit the reset switch and the 2nd time it comes up normally.  Reboot again, it does it again, cycle it after that, it boots up normally...
OK nm I am using the UUID listed from "dumpe2fs /dev/md0", which corresponds with the one in the menu.lst's comments actually...

```

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
timeout         3

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
# kopt=root=UUID=dc0b7815-7b07-4285-beb9-0cbdcc1ebbf1 ro
# kopt_2_6=root=/dev/md0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/md0 ro
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/md0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```




Also, here's /dev/md0:
```

root@sisko:/boot/grub# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Sep  8 14:57:31 2007
     Raid Level : raid1
     Array Size : 7815488 (7.45 GiB 8.00 GB)
    Device Size : 7815488 (7.45 GiB 8.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Sep 25 21:15:02 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : ed45e163:19f4bf9d:872c4c23:773967b8
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```

and /dev/md1:

```

root@sisko:/boot/grub# mdadm -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Sep  8 15:06:27 2007
     Raid Level : raid1
     Array Size : 480568320 (458.31 GiB 492.10 GB)
    Device Size : 480568320 (458.31 GiB 492.10 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Sep 25 21:13:38 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 01d7a385:d5469c1c:872c4c23:773967b8
         Events : 0.32

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2

```

---

### Post by spirilis on 2007-09-25
Nope, same problem--I booted using the UUID this time and it still did "array md0 already has disks!" nonstop, I hit reset, and it booted normally the 2nd time around (still using the UUID for root there).


This was the grub entry:
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=dc0b7815-7b07-4285-beb9-0cbdcc1ebbf1 ro
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

I am nearly at wits end here.  Why did this never crop up until just yesterday, when I've booted this system up a number of times over the past few weeks?  Something very fishy has to be happening here.


FYI, I tried deleting /etc/mdadm/mdadm.conf and running update-initramfs to see if that'd make a difference.  It doesn't, somehow update-initramfs regenerates /etc/mdadm/mdadm.conf with my default settings.
It seems this must be occurring somehow during the initrd stage...


I am giving "dpkg-reconfigure mdadm" a shot.  I specified to only bring up 'md0' during boot.  No idea if this will make any difference but we'll see.

---

### Post by spirilis on 2007-09-25
Hmmmmmm, very promising actually.  After performing the "dpkg-reconfigure mdadm" I have been able to successfully reboot the system 3 times without any "array md0 already has disks!" problems.  After the first reboot I switched back to using root=/dev/md0 instead of the UUID and it's still working.

Going to try once more... afterwards I am going to walk back through the dpkg-reconfigure and document here exactly what my answers were to the dialog boxes.

----

Yep, still works.

Here's what I did:

dpkg-reconfigure mdadm
For "MD arrays needed for root filesystem:" I just specified /dev/md0, NOT the 'all' keyword (which was the default).  I think this is the main difference between now and before.

"Do you want to start MD arrays automatically?" - yes

"Should mdadm run monthly redundancy checks of the MD arrays?" - yes

"Do you want to start the MD monitoring daemon?" - yes

"Recipient for email notification" - put my email addr in there

After this, it regenerated /boot/initrd.img-2.6.20-16-generic and /boot/initrd.img-2.6.20-15-generic:
```

 * Stopping MD monitoring service mdadm --monitor                                                                                                                                                                                       [ OK ] 
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
 * Starting MD monitoring service mdadm --monitor                                                                                                                                                                                       [ OK ] 
 * Generating udev events for MD arrays...                                                                                                                                                                                              [ OK ] 

```

Rebooted the system.  It booted the default 2.6.20-16-generic kernel with initrd, flawlessly with no "array md0 already has disks!" crap.
I see that it loads up md1 later, after initrd has finished and it's going through the rcS scripts.  It still detects my LVM Physical Volume on md1 and mounts all my LVM-managed filesystems correctly on bootup.
Works for me!


That must be one obscure and nasty bug though..... (anyone reported it yet?)

---

### Post by matthodge on 2007-10-03
Hello.

I'm having exactly the same problem with my RAID5 array in Ubuntu 7.04 64bit Server Edition.

Switch on the PC after it has been off all night and it just spams down the console screen "md: array md0 already has disks".

I press the reset button and the next time it boots it works fine. Very strange.

My question is will doing a **dpkg-reconfigure mdadm** cause me to loose the data on my array or will the data be safe (I've got 400GB of data on the array - loosing it would be bad bad bad.)

Thanks.

---

### Post by klausbreuer on 2007-10-26
I run a RAID-5 array.

This weirdo message "md: array md0 already has disks!" has shown up twice: once when I changed my Linux (from Gentoo to Ubuntu), and then after my motherboard blew out (apparently it didn't like Ubuntu as much as I do) and I had to replace most of the hardware.

I believe that it might be loading the drives in the wrong order, so to speak. If this is mixed up somehow at boot, it'll sometimes work - and sometimes not.

Here's what I did, and which worked both times:

First, shutdown the array:
sudo mdadm --stop /dev/hd0

Then tell it to read the RAID info from the hard drives themselves (not some config), and rebuild things (including the config?) automagically:

sudo mdadm --assemble /dev/md0 /dev/sda /dev/sdb /dev/sdc /dev/sdd (and so on, until all drives are included).

Have a look what he's doing:
cat /proc/mdstat

Voila! Took a while both times (couple of hours), but it ran flawlessly ever after :D

---

### Post by Ueland on 2008-02-02
*bump*

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/188392](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/188392)

Just reported a bug on this.

---

### Post by srt4play on 2008-03-24
Thanks spirilis for your input.  I encountered the "array already has disks" problem today on my 4 disk raid5.  Your solution of doing dpkg-reconfigure worked great.

---

### Post by SethA on 2008-03-25
That didn't fix it for me.

I'm having a similar yet slightly different problem that is probably compounded by my really weird setup.

I have 4 MD devices. Three are RAID1, one is RAID5. Most of my disk space is allocated to the RAID5. The RAID5 uses LVM to carve the array into swap, a couple of OS partitions, etc., and a large storage space for fileshares

I have a multiboot setup where I have a common /boot partition on a small RAID1. Due to previous hardware issues that created stability issues with root being on the RAID5, I thought it would be good sense to carve out a few gigs for an alternate OS installation on a RAID1 device--used basically only in a disaster scenario if I ever had to rebuild the RAID5 (which contains the real OS I run from day to day).

So the weird part is that when I boot to the RAID5 OS, I have no issue ever. If I boot to the MD1 device as my root and OS, I get the "every other reboot, it goes belly up with the md: array..... message" problem.

I've run dpkg-reconfigure twice. Once when booted into the RADI5 (MD3) install of the OS, and once when booted to the MD1 device. Just for good measure......  That didn't resolve the problem. The only difference in the options I selected is that I still selected "all" for the devices needed for root filesystem....I was afraid it would mess up my perfectly good working RAID5 installation if I only selected /dev/md1!

Now the other possibly contributing factor was that the UUID of MD1 had changed since I originally installed this whole setup. I can't remember what it was that prompted me to notice it. Perhaps is was me checking on the status of my disks, but I noticed that MD1 wasn't "up" or mounted. I couldn't bring it up either. I rebooted trying the MD1 OS and saw the problem reported above. I rebooted to the MD3 device, no problem. In fact MD1 came up this time with it....  So I ran:

mdadm --examine --scan /dev/sda2 

and compared the results against mdadm.conf and fstab. That is when I noticed that the UUID was mismatched. So I updated the mdadm.conf and fstab files (this is on my RAID 5 installation). That ironed out any lingering issues in the RAID 5 installation with mounting and starting the MD1 array. 

However, anytime I try to boot up on the MD1 installation, I get the same thing still. Yes, I have checked mdadm.conf and fstab and fixed those as needed for my OS that is on the MD1. I have gone over it several times to make sure.

I doubt anyone has the magic answer, so I won't even ask. I just thought I should share my experience too in case it helps someone.

[Edit]
Also found this:
[https://bugs.launchpad.net/ubuntu/+bug/140854](https://bugs.launchpad.net/ubuntu/+bug/140854)

Unfortunately, the fix listed doesn't help me as I don't have any mysterious UUIDs when I examine all my partitions. They all are correct, so there is nothing to zero out.

---

### Post by SethA on 2008-03-25
on a related note.... Can anyone tell me how to capture messages from (or pause) the bootup process. I want to examine and perhaps post the raid messages right before the "md: array md1 already has disks!". I think it shows the RAID configuration and that might give me a clue as to what it may be doing.

In Windows, you could hit the pause/break key to freeze the bootup in order to get a look at error messages before they flew off the screen. In Ubuntu (Feisty), the bootlog is broken I think. At least that is what I read and it explains why my log is always empty. Anyway, not sure how you can capture some of this vital info, but I bet someone knows how.....

---

### Post by SethA on 2008-03-25
One more comment. If you are patient, after a couple of minutes, you will see the busybox message fly up amidst the flow of md messages. If i type mdadm --stop /dev/md1 a couple of times after seeing that, then the stream of messages stops and I get the (initramfs) prompt.

From there, if I run any mdadm -D commands, all my MDs are up and running in the exact config they should be. Even MD1 is running although running the "stop" command on it! Running mdadm -E on all partitions shows no strange UUIDs. So something in the boot process is picking up some piece of info somewhere that is telling it that there are other partitions to add to MD1.............

---

### Post by hebetude on 2008-05-18
I had this problem and fixed it with 
mdadm --stop /dev/md0

/dev/md0 already has disks b/c it is already created and repeatedly attempting to create the raid for some reason.  After I stopped this the dmesg spam stopped and I was able to mount the array.

Just a FYI, if you bump your own thread it removes it from the unanswered queue thus making it more difficult to find for people to help you with ;).

Refer to bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/188392](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/188392)

This is a problem with a rebooted system which unlike the Windows world is difficult to test b/c our machines never have to be rebooted :guitar:

---

