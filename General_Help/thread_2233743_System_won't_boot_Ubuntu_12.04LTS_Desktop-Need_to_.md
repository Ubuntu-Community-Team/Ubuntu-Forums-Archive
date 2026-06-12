---
title: "System won't boot Ubuntu 12.04LTS Desktop-Need to fix GRUB"
date: 2014-07-10
forum: General Help
---

### Post by sewbiz on 2014-07-10
I am not sure I am in the right forum category. I am fairly new to Linux and have been working on this for 3 weeks now. It started when my Boot Disc was getting full. I have installed on my Desktop Ubuntu 12.04LTS and am now using Windows 8.1 Laptop to correspond here. I started a thread "GRUB RESCUE" under Installation category I believe, but now has 98 posts so was advised to start over. Please talk to me simply and dumb everything down because I am a beginner. 

WHAT I SEE:

Computer goes on ...I get the screen that shows my computer manufacturer (Intel) and the BIOS and BOOT menu keys....but then I get the black screen that reads:
error: file not found.
grub rescue> _    (and the curser is blinking)....the screen does recognize my keyboard but only understands one command...'ls'....all other things I have tried give me a message
that says "unknown command', 'bad file name', 'unknown file'...etc.

WHAT I DID TO CAUSE PROBLEM:
When my boot disc was finally 100% full I went to the Boot folder to remove old kernals I did not need. This was gaining positive results. I should have stopped there but I was
anxious and opened Grub folder too. When I saw the file folders with the music notes I was sure I didn't need them so started deleting (.mod files). I thought they were music files and know they take up a lot of space. STUPID, I know...but too late. Screen went black so here I am.

WHAT I HAVE TRIED:

Using UNetBootin downloaded from the website to my Windows 8 laptop, I installed the .iso file for the Ubuntu 12.04LTS to a folder (download) on my computer and then to a USB using UNetBootin for the drive transfer. My desktop did not recognize the USB or rather the boot priority was not changed to make sure it looked at that first. I can't change the boot priority because when I get to that screen on the desktop, the arrow keys won't let me select things to change it. The arrows work for some things but not others. So...the computer is seeing the keyboard. (Wireless) so it also must see the USB ports because the keyboard is wireless and has a thing in the port. (I have 7 avail ports). I burned boot repair disc.iso to a DVD-RW (and set the disc to burn "like a USB"). I put it in the drive for the desktop and it did not do anything to change the boot or correct anything/no fix.

FILES:    Ubuntu-12.04.4-dvd-amd64.iso      boot-repair-disc-64.iso
SPACE:  I have enough space on the USB.....did format disc auto on Windows 8.1
COMPUTER that has GRUB files missing:  Desktop   Intel    BIOS Version  

Other questions? Please help if you can....does this sound like my system is not bootable? Any hope?  Thank you in advance!

---

### Post by yancek on 2014-07-10
From your other post, you indicate that you have used the unetbootin software to successfully create a bootable flash drive.  One of your posts indicated you got the success message.  Your problem is that you cannot boot the flash from the old computer which had and probably still has an installation of Ubuntu 12.04.  The paragraph below is from my last post in your other thread.  You need to change the boot priority so that you can boot the flash drive.  If you cannot do that, it will continue to try to boot from the hard drive with the broken Grub bootloader and it will continue to fail. 

 Put the flash drive in your machine with the broken Grub then boot it. When you see the first screen, you should see an option at the bottom of the screen indicating which key you need to repeatedly tap to enter setup. If it is an intel, it may show intel on this screen.  On mine it shows HP as I have a Hewlett Packard, if it were a Dell you would see a Dell logo.  Those are examples.  Common keys are F2, F10 but there are others and it should show but only for a few seconds. If you are able to access your BIOS, you should see a Boot tab at the top. Use the arrow key on your keyboard to highlight it and look for Boor Priority and highlight it with the keyboard keys and look for options.  If you are required to enter a password at this point, that will need to be changed since you won't be able to modify boot priority without entering the BIOS.

---

### Post by Bucky Ball on 2014-07-10
The USB should be totally wiped prior to creating the USB with UNetbootin. If you have both these ISOs on it:

Ubuntu-12.04.4-dvd-amd64.iso boot-repair-disc-64.iso

You have somehow made a multi-boot USB, and I don't think that is the case. Please confirm.

Format the USB FAT32 and try again if the above is correct. By the sounds of the files you deleted, though, this could be tough! If you intend to simply reinstall, we should be able to get you there. ;)

---

### Post by Bucky Ball on 2014-07-10
*Thread moved to **General Help**.*

Also, your other thread has been closed. Please do not post duplicate threads. It causes confusion and reduces your chances of support.

---

### Post by yancek on 2014-07-10
> Please do not post duplicate threads.  It causes confusion and reduces your chances of support.

I suggested that the OP start another thread as the problem is unrelated to Grub.  The previous thread was called Grub Rescue.   After posting this, I noticed  that there was another post in a different section of the forum with the  same title as this one so I'm not sure which one Bucky Ball is referring to.  I expect the one with the same title.

This post is mis-titled because the problem is not Grub, but an inability to modify the boot priority in the BIOS.  Not sure if this is due to her unfamiliarity with the BIOS options or because there is a BIOS password unknown to the OP.  My understanding from her previous post is that she got Ubuntu successfully on the flash and was told when asked in her other post NOT to put the boot repair on it.  Don't know what actually happened.


 . 
Perhaps a moderator could change the thread title to something more appropriate.

---

### Post by sewbiz on 2014-07-11
> **yancek said:**
> I suggested that the OP start another thread as the problem is unrelated to Grub.  The previous thread was called Grub Rescue.   After posting this, I noticed  that there was another post in a different section of the forum with the  same title as this one so I'm not sure which one Bucky Ball is referring to.  I expect the one with the same title.

This post is mis-titled because the problem is not Grub, but an inability to modify the boot priority in the BIOS.  Not sure if this is due to her unfamiliarity with the BIOS options or because there is a BIOS password unknown to the OP.  My understanding from her previous post is that she got Ubuntu successfully on the flash and was told when asked in her other post NOT to put the boot repair on it.  Don't know what actually happened.


 . 
Perhaps a moderator could change the thread title to something more appropriate.

 If the moderator wants to change title to something more appropriate I appreciate the help.
Here is where I am at today. I am in my old system. I reinstalled Ubuntu 11.04 alongside my Ubuntu 12.04.4LTS. 
The .iso files were each on a separate USB and that was the only things on them.
I did figure out how to change the BOOT PRIORITY.  I could get to the BIOS page without password by just clicking "enter". Small details not mentioned
but made all the difference. I am grateful. 
My desktop boots only from my CD/DVD drive I think.
 Doing backups (pictures/movies) so will have to wait on this for a couple days.

I am thinking the next step is Boot-Repair Disc.iso . Maybe I can use the terminal commands for this.
I still have to fix Grub in my 12.04.4LTS partition, and change the Boot Priority to my computer not the drive.
I would rather be using 12.04.4LTS or another version of Ubuntu...eventually. That is my goal...full restoration
of BOOT and newly installed version of Ubuntu.

I will check in tomorrow. Thank you for all your help everyone! I am taking
notes so hope to add my experience with this problem to the Wiki community page. Things are looking up.

---

### Post by yancek on 2014-07-11
Since you have now managed to make changes in your BIOS, I guess your thread title is appropriate.
I'm not familiar with the BIOS on your computer.  My experience on all the computers I have used is that there is a message on the BIOS screen, almost always at the bottom of the screen telling the user to press "" key to 'enter setup'.  This generall requires repeatedly tapping the specified key.  Then using the arrow keys on the keyboard to get where you want and make changes.  My experience has been that at the bottom of the screen, it gives key options to save, usually the F10 key after the change, then of course the Enter key.  Glad you got that working.

So now you have Ubuntu 11.04 also installed, is that correct?  You went through the installation procedure and got a success message and an instruction to reboot?
You can determine if you are able to boot from the hard drive by removing the DVD from the drive.  If you have done that and rebooted without success, go back to the BIOS and change the boot priority back to the hard drive.  I have often had the CD as first boot priority and if there is no CD/DVD in the drive it would automatically boot from the hard drive.  Recently on one of my computers, I am no longer able to do this.  Have no idea why so now after using a CD/DVD, I change the boot priority back to the hard drive.  Try that and see what happens.

To be clear, it seems you are still unable to boot either 11.04 or 12.04 from the hard drive, is that correct.  Change the boot priority back to the hard drive, remove the DVD or flash drive before rebooting.  If you can then boot either 11.04 or 12.04, report back.  If nether boots, again boot one of the flash drives with 11.04 or 12.04.  Open a terminal and type the following command:  sudo fdisk -l (Lower Case Letter L in the command) , hit the Enter key. Post that output here as it will give information on partitions which might help.

---

### Post by sewbiz on 2014-07-13
> **yancek said:**
> Since you have now managed to make changes in your BIOS, I guess your thread title is appropriate.

So now you have Ubuntu 11.04 also installed, is that correct?  You went through the installation procedure and got a success message and an instruction to reboot?
You can determine if you are able to boot from the hard drive by removing the DVD from the drive.  If you have done that and rebooted without success, go back to the BIOS and change the boot priority back to the hard drive.  I have often had the CD as first boot priority and if there is no CD/DVD in the drive it would automatically boot from the hard drive.  Recently on one of my computers, I am no longer able to do this.  Have no idea why so now after using a CD/DVD, I change the boot priority back to the hard drive.  Try that and see what happens.

To be clear, it seems you are still unable to boot either 11.04 or 12.04 from the hard drive, is that correct.  Change the boot priority back to the hard drive, remove the DVD or flash drive before rebooting.  If you can then boot either 11.04 or 12.04, report back.  If nether boots, again boot one of the flash drives with 11.04 or 12.04.  Open a terminal and type the following command:  sudo fdisk -l (Lower Case Letter L in the command) , hit the Enter key. Post that output here as it will give information on partitions which might help.

I have both 11.04 installed and 12.04. It does not boot from the hard drive. Changed boot priority and now it does but brings me to only my broken program (ubuntu 12.04 LTS) and with a terminal on the page...nothing else. I typed in sudo fdisk -l and this is what I get:

Disk /dev/sdb: 500.1 GB,......bytes
244 heads,...track....cylinders...total...sectors
Units = sectors....blah blah blah...
Sector size....
I/O size...
Disk identifier:....
Device Boot    Start     End    Blocks   Id   System
/dev/sdb1  *         ...      ...      ....    ..   Linux
/dev/sdb2                                            Linux
/dev/sdb3                                            Linux swap / Solaris
/dev/sdb4                                            Linux

Disk /dev/sdc:  .....MB,  ....bytes
122 heads,...track....cylinders...total...sectors
Units = sectors....blah blah blah...
Sector size....
I/O size...
Disk identifier:....

Device Boot    Start     End    Blocks   Id   System
/dev/sdc1 *     8064    ....      ....        c   W95 FAT32 (LBA)

I can fill in the other info if you need it. What am I looking for? Thank you for your help.

---

### Post by Bucky Ball on 2014-07-13
Do you need to login at that cursor? If you do, once you've logged in, type 'startx'.

---

### Post by sewbiz on 2014-07-14
Forgive me...I am so confused now about what to do. Because I have now both Ubuntu versions on my computer, although my system does not boot on it's own, it does get me to a version if I select it....after pressing F10 on the keypad...but not on it's own. I have now about six choices, this time I chose the one at the top of the list.

I think I have to remove kernels from Grub first shouldn't I so my boot volume is no longer full. It is 100% full and why I think no matter what other steps I take, it is never going to boot. This is where this all started (many posts ago and over now 100 threads and many weeks). Very discouraged but know all is not lost as my system is working and responding.
I appreciate your help.

To remove kernels I did... uname -r     it told me the latest kernel   3.2.0-64 generic-pae       but that was for another version (maybe the 11.04 on my system in another partition)
I opened my 12.04 partition and put in the same commands but got a different result:
2.638-8-generic

Then I did      'grub ls'   and it said   The program 'grub' is currently not installed. You can install it by typing: sudo apt-get install grub
I did that and it said.....Package grub is not available, but is referred to by another package. This may mean that the package is missing,
has been obsoleted, or is only available from another source. However the following packages replace it:
grub-pc
E: Package 'grub' has no installation candidate

When all this began...and my boot volume disc was full, I removed files in Grub (.mod files...and others perhaps) that I should not have.
I also removed old kernals. So, I am thinking, I need to fix GRUB first and foremost. Am I right?

---

### Post by sewbiz on 2014-07-14
This is what I get when I type in this command ( how do I know where the disc partition is that has my boot?)

Command line:     sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512= 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x000c8cf3
Device Boot        Start   End Blocks  Id  System
/dev/sda1  *                                                   Extended
/dev/sda5                                                        Linux
/dev/sda6                                                        Linux
/dev/sda7                                                        Linux
/dev/sda8                                                        Linux
/dev/sda9                                                        Linux swap / Solaris
Partition table entries are not in disk order
Disk /dev/sdb:  500.1 GB, 500107862016
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512= 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x000dab0f
Device Boot        Start   End Blocks  Id  System
/dev/sdb1  *                                                   Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2                                                        Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3                                                        Linux
/dev/sdb4                                                        Linux
Disk /dev/sdc:  7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders, total 15240576 sectors
Units = sectors of 1 * 512= 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0xc3072e18
Device Boot        Start   End Blocks  Id  System
/dev/sdc1  *                                                   W95FAT32 (LBA)

---

### Post by Bucky Ball on 2014-07-14
Forget about 11.04. Not supported. Stick with trying to resurrect 12.04. Choose the kernel at the top of the list, not at the bottom. 

I'm starting to get as confused as you, but can you actually get to a desktop when you choose the first kernel on the list? The things is, finding your list of kernels is fine, but not if you don't know the kernel you are currently booted into. You run the risk of attempting to remove it. This will tell you:

```
uname -r
```

The 2.*.* kernels are for 11.04 I would think. 3.*.* are 12.04. If you are running 2.*.* you've booted to the wrong kernel (like I say, 11.04 is not supported by Canonical, nor do we give support for it here). 

In the output above you also have these errors:

```
dev/sdb1 * Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2 Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
```

This could be a problem I'm presuming you are booting 11.04 on one disk and 12.04 on the other? When you are booted into the 12.04 install (and you know you are) run:

```
sudo grub-install /dev/sda
```

That will make sure the grub is 12.04's and not 11.04's.

The way I normally get rid of unwanted kernels is to find which one I'm using, open Synaptic Package Manager (you might need Software Centre) and look for 'linux image'. That should give you a list of all kernels available and installed. Simply remove the ones you aren't booted into. Before doing this I'd advise booting into 11.04 and backing up any important data that's in there. You would ideally want to remove that partition as, as I say, 11.04 is a dead duck and I wouldn't advise continuing with it.

Only keep the linux image you are using and the one prior to it. E.g. if you are using 3.13.0-30-generic then you would keep that and 3.13.0-29-generic. This is so if the -30 kernel falls over for some reason, i.e. dodgy update, then you have a working kernel to fall back on. 

Hope that helps, but your current situation looks a bit murky from here. :-k ;)

---

### Post by sewbiz on 2014-07-14
> **Bucky Ball said:**
> Forget about 11.04. Not supported. Stick with trying to resurrect 12.04. Choose the kernel at the top of the list, not at the bottom. 

I'm starting to get as confused as you, but can you actually get to a desktop when you choose the first kernel on the list? The things is, finding your list of kernels is fine, but not if you don't know the kernel you are currently booted into. You run the risk of attempting to remove it. This will tell you:

```
uname -r
```

The 2.*.* kernels are for 11.04 I would think. 3.*.* are 12.04. If you are running 2.*.* you've booted to the wrong kernel (like I say, 11.04 is not supported by Canonical, nor do we give support for it here). 

In the output above you also have these errors:

```
dev/sdb1 * Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2 Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
```

This could be a problem I'm presuming you are booting 11.04 on one disk and 12.04 on the other? When you are booted into the 12.04 install (and you know you are) run:

```
sudo grub-install /dev/sda
```

That will make sure the grub is 12.04's and not 11.04's.

The way I normally get rid of unwanted kernels is to find which one I'm using, open Synaptic Package Manager (you might need Software Centre) and look for 'linux image'. That should give you a list of all kernels available and installed. Simply remove the ones you aren't booted into. Before doing this I'd advise booting into 11.04 and backing up any important data that's in there. You would ideally want to remove that partition as, as I say, 11.04 is a dead duck and I wouldn't advise continuing with it.

Only keep the linux image you are using and the one prior to it. E.g. if you are using 3.13.0-30-generic then you would keep that and 3.13.0-29-generic. This is so if the -30 kernel falls over for some reason, i.e. dodgy update, then you have a working kernel to fall back on. 

Hope that helps, but your current situation looks a bit murky from here. :-k ;)

I did what you said and do understand most of what you are telling me (been studying the manual for over 4 weeks now). I am in my 12.04LTS but had to manual boot it. It is broken. These are the steps I took:

Turned off computer (clicked to "restart")
F10 key
Password page came up (not for desktop but to get to the Boot Device page)..clicked enter (no password needed)
Boot Device: PATA:Hitachi HDP######....
Kernel Page: Ubuntu w/Linux 3.2.0-65-generic-pae
This version is broken for me....I only get a terminal and the sign on page but it never opens.
```
uname -r
3.2.0-65-generic-pae
sudo grub-install dev/sda
```
Grub device was installed, finished, no errors. This is the contents of the device map /boot/grub/device.map
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script 'grub-install'
```
(fd0)   /dev/fd0
(hd0)  /dev/sda
(hd1)  /dev/sdb
(hd2)  /dev/sdc
```

##The last part I don't understand..."check if this is correct"...I don't know what (fd0) is for. I am stuck.
When I write on the command line 'grub-install' after that I get this message:
```
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.
```

Maybe I need to write more info on my command line...not just 'grub-install'.....maybe....'grub-install  /dev/sda'  or something like that?
Thank you for your patience. How do I remove Ubuntu 11.04 now that I have it reinstalled (although it is no longer supported, it gets me
to my desktop)? apt-get remove? sudo remove? I know
some things...and learning others the hard way. I understand about kernels and how to be careful not to remove recent ones. I do
have things backed up so ready to proceed to whatever next step I need to take. REMINDER: My GRUB is a mess...missing files I deleted...also
NO VOLUME LEFT ON BOOT DISC TO BOOT my computer. 

I will walk away from this and give everyone time to respond before I mess things up further. : (  
I do appreciate your help unmeasurably!!!

---

### Post by Bucky Ball on 2014-07-14
I think you're making this a bit more complicated than it is. You used the wrong command which is why you got this:

```
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.
```

You only used the first part of the command I gave you:

```
sudo grub-install /dev/sda
```

... which specifies where to put grub: /dev/sda - first part of the first hard drive. 

Please use [code][ /code] tags around terminal output. Neater and much easier to read. Thanks. I have added them manually to some of your last post so you can edit and see how, but you can also use 'Go Advanced' or 'Adv Reply', highlight the code and click the # icon.

---

### Post by sewbiz on 2014-07-14
> **Bucky Ball said:**
> I think you're making this a bit more complicated than it is. You used the wrong command which is why you got this:

```
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.
```

You only used the first part of the command I gave you:

```
sudo grub-install /dev/sda
```

... which specifies where to put grub: /dev/sda - first part of the first hard drive. 

Please use [code][ /code] tags around terminal output. Neater and much easier to read. Thanks. I have added them manually to some of your last post so you can edit and see how, but you can also use 'Go Advanced' or 'Adv Reply', highlight the code and click the # icon.

I am sorry. I know I am not that bright when it comes to Ubuntu. Please show me which thread I missed that shows the second part of the command I was suppose to put in. I am very new at Linux so everything has to be explained step by step. I am happy to go to a linked page in the manual that would explain everything to me. Believe me I am trying very hard to find my own solutions. I do appreciate your help. Not everyone uses the brackets around code as you do so this is the first I have come to know about proper technique for communicating what I did. Still learning all things new about Linux.

---

### Post by yancek on 2014-07-14
> sudo grub-install dev/sda

The above command is what you indicated you entered to install Grub to the master boot record of sda.  The command below is what was suggested to use.  Note that you need the forward slash (/) before the dev as shown below:

> sudo grub-install /dev/sda 

Commands in a terminal need to be exact.  Spaces where needed, putting spaces where they don't belong, etc. will all result in errors.
You asked what fd0 meant, that refers to floppy drive and there is no reason to deal with it.  The uname command suggested above will tell you which kernel you are using.  If you boot into whichever Ubuntu works, open a terminal and copy/paste the code below:

```
 cat /etc/issue
``` 

If it is 12.04 you will see the output below:

```
Ubuntu 12.04.2 LTS \n \l
```

If it is 11.04, that will show up.  To find out which partition you are on, copy/paste the following in a terminal:

```
df -h
```

It will show output similar to below.  The example below shows the root partition under the column Mounted on, signified by the root symbol:  /
On the left of that row, under filesystem, it will show the partition the filesystem is on.  The example below shows sda5.  Make a note of this information on your system.  You should also be able to see boot under the Mounted on column if you have a separate boot partition and the partition it is on under the filesystem column.

```
 df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        19G   15G  3.7G  80% /

```

If you find that you are on 12.04, you can then run the grub-install command suggested above.

---

