---
title: "How To Set Up Your Ubuntu 6.06 Server To Run RAID-1 With Live Data"
date: 2007-06-10
forum: General Help
---

### Post by KingJohn on 2007-06-10
subtitle:  Why I Am Smarter Than My Server, This Time.


**Quick basics:  **Why is this not simply a reply to [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
Because that one doesn't let you keep your existing data.

Why is this not in the forum for Tips + How-Tos:  Because I'm not sure if it qualifies based on the rules there,  and it's not for the most recent Ubuntu, nor am I going to test it on the most recent one.  Sorry, I don't have the hardware to spare for that kind of testing.

Why am I posting it if it's not good enough for the Tips forum:  Because I think it might be handy for anyone going through the process in the future, and I didn't find anything quite like this when I went looking.

**On to the post:**

I have a Ubuntu server.  It does many server-things, but has only one hard drive.  I want it to have two hard drives, and I want them to be RAIDed together in a RAID-1 configuration, which is to say a mirror.  Since nobody is buying me a hardware RAID controller, I am doing this through software.

There are many, many suggestions on how to do this on the internet.  None of them are for Ubuntu, as far as I could find.

First things first:  Go to [http://alioth.debian.org/download.php/668/rootraiddoc.97.htm](http://alioth.debian.org/download.php/668/rootraiddoc.97.htm) and take a look at this document.  It is a how-to for RAID-1 in Debian, and particularly for an old version of Debian - but it's also a great start.  This document is, in fact, all you need.

I'm writing this anyway, to tell you where that document lies.  Why does it lie?  Because it's for Debian, and Old And Busted Debian at that.  I am working with New Hotness Ubuntu, meaning some of that document's assumptions do not apply.  One assumption that DOES apply, though, is that your two drives are identical.  Same manufacturer, same model, same everything;  identical.  If they're not identical, then you'll need to do your best to make them identical, and you'll need to accept that you're going to lose a little potential drive space on at least one of them.  Oh, yes, and you need to be root.  Either use "sudo" in front of every one of these commands, or use "sudo su" before you start, but be root.

**STEP 0:  BACK EVERYTHING UP AND MAKE SURE YOU HAVE A BOOTABLE LIVECD HANDY.**

This should be self-explanatory.  You CAN (and I did) do all this remotely, but if you screw up at any stage, you're going to need to be in front of your machine to fix it because it might not boot right, and you very well might be losing data.  All your data. 

Also, schedule some downtime.  You're going to be rebooting more often than a Windows ME machine trying to upgrade to Vista.  Yes, rebooting.  It's the only way to be sure.

**STEP 1:  "Install Debian"**

This is a lie.  Step 1 is that you install *Ubuntu*, and you do so using the "Alternate" image, and you select RAID during installation and it does all the magic for you, in advance, and you don't need the rest of this document.  My entire post is predicated on the assumption that you have already ****** up STEP 1 by installing Ubuntu *without* using those handy RAID shortcuts, and that you have a working system with no RAID.

**STEP 2:  "Upgrade to a RAID savvy Kernel"**

Luckily, you're running Ubuntu 6.06.  That means you've already got one, or, at least, that *I* already have one.  2.6.15-28-server, in fact, when I did this, so if you've got that, you're good.  Test it, as the document suggests, with ```
cat /proc/mdstat
```If that returns a sensible-looking result and not an error message, you're good.

My copy came with mdadm.  If you don't have it, install it with ```
apt-get install mdadm
```

**STEP 3:  "CREATE RAID (fd) PARTITION ON HDC"**

That document assumes that the drive you HAVE is /dev/hda, first IDE master, and that the drive you're adding is /dev/hdc, second IDE master.   I like this convention, and so I will use it.  It doesn't actually matter where the drives are, and this should work equally well no matter where the drives are or whether they're IDE, SCSI, SATA, or what.  The important things to remember are that:  The drives should not be in the same IDE chain, and there should not be any slaves on the chains if the drives are the master because some BIOSen will, if the master dies, see a slave with no master and stop everything until they work that **** out.  Neither one of these are conditions that will stop you from making a RAID.  They just might be a royal pain in your *** in the future.

use ```
fdisk /dev/hda
```and then type "p" to get a list of the partitions on the current drive.  Press "q" to quit.
use ```
fdisk /dev/hdc
```to get to the new drive.  If it has any partitions, delete them, and then add new partitions that match the numbers on the previous partitions, exactly.  My source document suggests using ```
sfdisk -d /dev/hda | sfdisk /dev/hdc
``` which SHOULD work in principle, but I didn't do that because I didn't find that doc until after I'd manually copied the partitions.

Use "t" to change partition type, choose the first partition, select "fd".  Repeat for every partition that's going to be part of the RAID.  Check your answers with "p".  Make sure you mark your new boot partition as bootable.

When you're done with fdisk, hit "w" to write your changes to disk and exit.  EXPECT an error message about being unable to read the drive because it's in use.

**REBOOT HERE.**

Creating the actual RAID device is easy.  Your first disk partition is always hda1, so NATURALLY your first RAID "partition" will have a 0.  Get used to it, and triple-check all your commands before you hit enter.
Use```
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/hdc1
``` to create the first RAID device.  This device will have /dev/hdc1 (new, empty, partition 1) and, eventually, /dev/hda1 (old, full, partition 1) as it's components.  Right now, the keyword "missing" means that you're STARTING the array in degraded state, with only one drive.
Repeat this command for /dev/md1 (and /dev/hc2) and /dev/md2 and /md3 etc etc etc, until you've created as many RAID devices as you're going to want to use, in the end.

Format the new RAID drives with mkfs.  I like ext3, source doc likes reiserfs, you could probably use FAT32 if you had a masochistic streak, but that's not the point.  The command to do this with ext3 is ```
mkfs.ext3 /dev/md0
```Again, repeat the command for every one of your new RAID devices.

 Use **cat /proc/mdstat** to see your RAID devices - ensure they're all there, there's no error messages, and they all show as being degraded and missing a drive.

**STEP 4: COPY YOUR DEBIAN SYSTEM**
Obviously, we want Ubuntu, not Debian, but I'm sure you get the point.

His doc assumes a single RAID.  I assume multiple RAID devices, but the principle is the same:  Create a mount point for each device, mount each device, and copy the right data over into the right partitions.  The source document has it easy - everything's on one partition, so he just uses```
cp -axu / /mnt/md0
```Mine was a little more complicated - I had /boot on /dev/hda1, / on /dev/hda2, and /home on /dev/hda3.  This means I needed to use```
cp -axu /boot /mnt/md0
cp -axu /home /mnt/md2
```... and then a LOT of individual "cp -axu" statements for the other folders.  DO NOT copy /proc, /sys, /media, /mnt, or /dev.  Also, don't copy anything else you had on a different partition - in my case, /boot and /home.

Don't forget a final ```
cp -au / /mnt/md1
```(where you replace /mnt/md1 with your new root RAID partition) to get anything actually sitting in / out, at the end.
About those switches on copy:  -a is CRITICAL.  It means "retain ownership and permission".  -x means "recurse and include subdirectories".  -u just means "update" - don't copy a file if it's already at the destination.  It's completely useless the first time, but if for some reason you need to run the command again, it will save you a lot of time instead of overwriting stuff you've already copied.

4.4: EDIT /etc/fstab TO MOUNT THE NEW RAID ON BOOTUP

Uh, yeah, do this one.  It's totally not NECESSARY, but it's an excellent sanity test - and when you're screwing around with a live machine's boot and root partitions, you need all the sanity tests you can get.

**REBOOT HERE**

use ```
mount
```to ensure that your raid partitions mounted properly after the reboot.  Use **cat /proc/mdstat** to see your RAID devices - ensure they're all there, there's no error messages, and they all show as being degraded and missing a drive.

**STEP 5. REBOOT TO RAID DEVICE**

Whoo, mama, here's where the changes start.
To begin with, if you're using Lilo, you're SOL.  Follow his instructions and hope they work, because I use Grub and I didn't use them.  If you use Grub, jump forward to PART II.

There's good news and bad news.  The bad news is, Ubuntu doesn't come with mkinitrd, and doesn't have it as a package.  The good news is, the version of Ubuntu I'm using doesn't actually *need* it.  The doc is telling foolish Debian lies again.  Ignore this order - as far as I know, you don't need to worry about it.

*DO* update /boot/grub/menu.lst, like it tells you to, though, and edit /etc/fstab to put your new root partition in place of the old root partition.  Do this for the boot partition, too.  Do *NOT* update any of the other partitions at this time, just root and boot.  You could do the rest now, but we're taking baby steps, as a sanity test.

**REBOOT HERE**

Use ```
mount
``` to see if root mounted properly.  If it did, be happy.  If it did not, do NOT proceed until you can get the system working from root on that device.  If it worked, this is probably a good time to set /etc/fstab to mount everything ELSE from the RAID devices, reboot again, make sure that everything is running off the RAID and that everything is working.  This is your chance to ensure that all your data got over to the new disk, and that everything works without the old disk involved - and it's your last chance to do so while your old disk is still untouched, in one piece.

**STEP 6: REFORMAT hda AS fd AND DECLARE IT AS DISK ONE OF YOUR RAID**

Yeah, here's the fun part:  We're reformating our original clean drive, which has, until now, been untouched.

Follow the source doc's fdisk instructions - they use cfdisk, I use just plain fdisk, but it's all the same thing - and set all the soon-to-be-RAIDed partitions to be of type fd (Linux Raid Autodetect), just like you did for your new drive back in Step 3. 

Add the drive parts to the RAID with ```
mdadm --add /dev/md0 /dev/hda1
``` and similar commands for /dev/md1 and /dev/hda2, etc etc.
Use ```
cat /proc/mdstat
``` to see the current status of the RAID - you should see that the disks are each, in turn, copying all the data from the *new* disk to the *old* disk - which is what we want, since we copied everything to the new disk in Step 4 and we just reformatted the old disk a second ago.

**WAIT**.  Under no circumstances are you to do anything else with your system until /proc/mdstat tells you that the RAID is complete, in one piece, and working, and done syncing.  Use ```
watch cat /proc/mdstat
``` if you want, and get a good book while you wait if your drive is a large one.

**STEP 7:  PUTTING GRUB ON THE SECOND DISK**

Installing grub into the second disk is, at this point, the way to go.  Run ```
grub
grub> device (hd0) /dev/hdc
grub> root (hd0,0)
grub> setup (hd0)
```

**REBOOT HERE.  ALSO, PRAY TO WHATEVER GODS YOU SERVE**

If you're like me, then at this point the machine *will* come back up, and it *will* work perfectly, and you will not have lost any data.  From here, you can test it by unplugging a drive and seeing if the other one comes up, just like the source doc tells you to.  I haven't done that yet, although it's in the cards for tomorrow morning, but everything else is working and everything looks good - the system is booting from the RAID, both halves of the RAID are identical in every way and they're both individually bootable, and the BIOS is set to go to each HDD in turn, so everything SHOULD work.

If you're not like me, then at this point your mission, should you choose to accept it, is to start over from your liveCD, put a RAID in first before adding data, and then restoring from those backups you made way back in Step 0

---

### Post by Midahed on 2007-07-19
KingJohn,

Thanks for an excellent post.  It has enabled me to get my live 7.04 Feisty Desktop system RAIDed without the need for a clean install.

I found one area where your procedure didn't work for me.  I may be wrong, but I think that's because the server edition comes with an initrd that already contains the RAID modules, whereas the desktop version doesn't.

It took me days and days to actually get it working (mainly because I'm new to Linux), but it runs like a dream now and boots off either drive.

I've posted the gory details here [http://ubuntuforums.org/showthread.php?p=3044409](http://ubuntuforums.org/showthread.php?p=3044409) and made reference to your excellent guide and two or three other documents which provided essential information during the process.

Thanks again,

Mike

---

### Post by greg3000 on 2007-08-15
Hello from a 2 day old ubuntu 7.04 linux server user here.  Thanks for the great information, I will use it next time.  For my first setup I've used the following link: [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

I've got a raid 1 array consisting of 3 partitions, MD0 is a 10gb boot, MD1 is a 10gb swap, MD2 is a 480gb /home 

I've got this system set to boot into ubuntu desktop and I'm currently testing the system for failure scenarios.  When I unplug either my main or secondary drive of this raid 1 array, tty fails to boot, so I get a busybox shell prompt and cat /proc/mdstat tells me that md0, md1, and md2 are inactive.  I understand that normal operations should really continue with a failed drive.  Could I ask the community to help me through this?

Thanks, I'm really excited to move my data from windows but not ready until I know the raid 1 is performing correctly.  

Thanks in advance :)
Greg

---

