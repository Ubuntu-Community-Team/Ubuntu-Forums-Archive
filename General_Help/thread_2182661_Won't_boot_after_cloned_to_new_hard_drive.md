---
title: "Won't boot after cloned to new hard drive"
date: 2013-10-22
forum: General Help
---

### Post by mmcl26554 on 2013-10-22
Ubuntu 12.04lts with Win7 WUBI.   Has been working just fine.  I recently installed and cloned to the new drive using Acronis home 2013.  I have done this before without any problems.  But now there is a boot problem I get the following error:
 ```
No such Device 50C25888C2587466
Press any key to continue
```
When I press any key nothing happens.  I tried "Boot Repair" but it didn't fix it and actually seemed to have some errors which I couldn't identify.   I am probably not an absolute beginner, but none the less a beginner so maybe a little more detail in the answer would help me learn.
I have been doing some studying on the internet and found some information about this and editing "UUID's".   I can boot the computer with the old hard drive via USB as I haven't deleted anything off it yet.   So as I understand I would be able to edit the necessary files from that boot.  If that is the case I will need some directions on what to do.  I do know how to edit config files as I have done some of this with "Samba".   
Thank you for any anticipated help.
Michael

---

### Post by ibjsb4 on 2013-10-22
I have never used Acronis, so no help there.  But I do use [clonezilla]("http://clonezilla.org/").  

With clonezilla, I must clone the entire drive (not just the partition) in order to include the boot (grub).

Also I cannot have the clone and original HDD plugged in at the same time, this will cause havoc.

---

### Post by mmcl26554 on 2013-10-22
I have seen you or someone else toot the horn about Clonezilla during my research on this issue.   However, there are probably more similarities between the 2 than differences.   Acronis, when it clones, it does do the entire drive including MBR, and will expand or compress the size to fit in the destination drive unless of course there is more actual data than the destination can hold.   I have cloned this drive before without problem to either OS.  I am wondering if Ubuntu is looking to connect to the old drive and not finding it stalls.   But it didn't have any problems previously connecting to a different drive, so I suspect something was corrupted in the process but I don't know what and that is why I have posted here in the hopes someone with more experience with Ubuntu then I have (and it won't take much to know more than I do about it), can help me resolve the problem.   So I am just awaiting for some assistance.
Michael

---

### Post by ibjsb4 on 2013-10-22
After you get 'Error: no such device' do you get the option to go to recovery mode?  Maybe not worded like that.

If you can get to a terminal/console you can try:

```
sudo fdisk -l **and** sudo blkid
```

If you get this far, please post the output.

This is for the clone hdd only.

---

### Post by mmcl26554 on 2013-10-22
The error message is an exact quote.   It says to press "any key" (of course there is no "any key" on the keyboard... HaHaHa) seriously, no matter what key I press it does not go any further.   So the only way I can change anything is to boot from a live disk or the system on the USB drive.  So that is where we will have to go to fix anything.   Recovery mode is not offered only what I have stated in the original post is all that is on the screen.   No recovery mode, no response to any key press.
Michael

---

### Post by oldfred on 2013-10-22
Do not connect original drive, but use liveDVD or flash drive and from Boot-Repair run the Boot-Info report and post its link.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jamesisin on 2013-10-22
Do try boot-repair as oldfred suggests; it really kicks asp.  It might also be possible that your clone was corrupted.  Will it be possible to create a new image from the original?

---

### Post by whitesmith on 2013-10-22
> **ibjsb4 said:**
> But I do use [clonezilla]("http://clonezilla.org/"). With clonezilla, I must clone the entire drive (not just the partition) in order to include the boot (grub).Just to clarity, clonezilla allows partition cloning, as well as whole-disk cloning. Of course, you'd have to have set up a separate /home partition to do this, as most experienced Linux users do.The options, as I recall, are named  clonepart (for a partition) and clonedisk (for the whole thing). Also, the clonezilla folks claim to be working on a feature that will allow recovery of individual files, as Norton Ghost does for Windows. Cheers!

---

### Post by mmcl26554 on 2013-10-22
I do have a "Boot Repair" disk and I did run it.   However, it didn't fix it and it couldn't activate my wireless card and it wanted me to connect to a wired system.   That wasn't convenient at the time and anyway if it worked would have been moot.   However, I'll run Boot Repair again with the laptop connected to a wired network and post the results.   Do you want just the URL or the complete listing?  I'll do it later this evening or tomorrow.   Thanks all of you people for your responses.
Michael

---

### Post by oldfred on 2013-10-22
Just need the link. Output is rather long.

---

### Post by mmcl26554 on 2013-10-22
I have looked at them in the past and they sure are long, that's why I asked.
Michael

---

### Post by bcbc on 2013-10-22
When you boot hold down the SHIFT key, press E on the first entry. There should be something like this:
```
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root 18B4B7BBB4B799A8
        loopback loop1 /ubuntu/disks/raring.disk
        set root=(loop1)
        linux   /boot/vmlinuz-xxx root=UUID=18B4B7BBB4B799A8 loop=/ubuntu/disks/raring.disk ro   quiet splash $vt_handoff
        initrd  /boot/initrd-xxx.img
```
Change the root= in the line /boot/vmlinuz-xxx root=UUID=[COLOR=#000000][FONT=Ubuntu Mono]50C25888C2587466[/FONT][/COLOR]
to look like:
root=/dev/sda3

You will have to figure out which /dev/sdaX it is, but you can get the hint from the line: set root='(hd0,msdos3). e.g. hd1,msdos2 is /dev/sdb2 and hd0,msdos1 is /dev/sda1

Then press CTRL+X to boot, and run sudo update-grub to fix after booting.

---

### Post by mmcl26554 on 2013-10-22
Good new bad news,
I was able to get to the listing and edit it But, I could not figure out how to save the changes because I got the same error message and when I went back into the edit screen it was back to where it was before I edited.   So it didn't stick.  So if there is a command to save the edit I don't know what it is and the Ctl X didn't do it.

Also others have told me to run Boot repair but that starts off with 3/4 page of errors at logical block 86902.   When it does boot up it says:
```
can't find file /mnt/boot-sav/WUBI1/home
```
In the end it cannot connect to the internet and send the data, even though the browser it loads can access the internet.  


So I still need a little more help but I think I'm on the right track if I can just get the changes to stick.

Michael

---

### Post by bcbc on 2013-10-22
Ctrl+X will tell grub to boot your modified entry.

Boot-repair won't help, because it doesn't have code for this sort of thing and is very limited with what it can do for Wubi installs.

---

### Post by mmcl26554 on 2013-10-23
Well then it's not working I have made the changes you suggest (several times) and I get the same error message as soon as I hit ctl X.  I have determined that the sda is 1 but I have also tried 2, and
```
set root= '(hd0,msdos2)'
```
so that should be sda1?
Just to confirm I am doing it correctly, I select the Ubuntu OS, the press the enter key and immediately press and hold the Shift key and when I see the first line on the screen press the "E" key.  Then the grub menu comes and I highlight the first entry which is the boot Ubuntu and press the "E" key again to get the listing to edit.  I edit the line you said to and press the Ctl+X key to boot and I get the same error message when the boot begins.   Is the the correct procedure?
What should I do next?
Michael

---

### Post by bcbc on 2013-10-23
(hd0,msdos2) is /dev/sda2 (the drive numbering starts at zero, but not the partitions)

So make sure the line looks like (remove the UUID= after root=):
/boot/vmlinuz-xxxx root=/dev/sda2 loop=...

---

### Post by mmcl26554 on 2013-10-23
No joy in mudville!

I made absolutely certain I have followed your directions but the only thing that changes is a new line is added at the top of the error message which says "booting a command list"  and that is the only thing that changes.    What is the long number begining with 50C anyway?
What is the next move.
Michael

---

### Post by bcbc on 2013-10-23
It's the UUID of the partition. Wubi boots via Grub2 with the config and modules on the actual root.disk, and it uses the UUID to identify the host partition because it's generally more reliable than the /dev/sdXY designation.

If you move a root.disk or modify the host partition in such a way that the UUID changes, it will fail to find the kernel. Note that it still finds the root.disk (that gives you the menu) because it uses two methods: first it tries the (hd0,msdos2) (i.e. /dev/sda2) and then it has a "search ..." line that tells it to set root to the partition with the given UUID. So even if that fails, it's already got the host partition. But the linux command will still fail.

Anyway long story... you can boot any root.disk since Ubuntu 11.10 using these generic commands (just hit C to get to the grub command line):
```
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

---

### Post by mmcl26554 on 2013-10-23
It is getting late here 1:20AM so I'll do it tomorrow and report back.  I assume I must   run sudo update-grub to fix after booting, Which I will do.
Thanks
Michael

---

### Post by mmcl26554 on 2013-10-23
> **bcbc said:**
> It's the UUID of the partition. Wubi boots via Grub2 with the config and modules on the actual root.disk, and it uses the UUID to identify the host partition because it's generally more reliable than the /dev/sdXY designation.

If you move a root.disk or modify the host partition in such a way that the UUID changes, it will fail to find the kernel. Note that it still finds the root.disk (that gives you the menu) because it uses two methods: first it tries the (hd0,msdos2) (i.e. /dev/sda2) and then it has a "search ..." line that tells it to set root to the partition with the given UUID. So even if that fails, it's already got the host partition. But the linux command will still fail.

Anyway long story... you can boot any root.disk since Ubuntu 11.10 using these generic commands (just hit C to get to the grub command line):
```
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```



Thanks to bcbc the issue is solved!   The code you sent worked and I did the update to grub and now it boots just fine.

Now I only have one problem left to solve would you please look at my Thread: [HTML]Vista (32) won't boot after 12.04 dual boot install[/HTML]
(Is this correct wrapper to use for text?)
If this thread is in your area of expertise can you help me here also?
Michael

---

### Post by bcbc on 2013-10-23
Glad you got it working.

Regarding the other thread, with 130+ posts... and already the assistance of many of the forum's experts - not sure I can contribute much. 
The huge delay in the grub menu showing up and Ubuntu booting is not good. That points to either some device incompatibility or drive/motherboard issue. I'd begin by getting a full list of hardware (brand,model, wireless, graphics card, monitor, etc.) and searching to see if other people have had the same problem. (This rules out a hardware failure and also might turn up an easy workaround). The fact that Vista boots fine probably means it's an Ubuntu/hardware compatibility issue.
Why Grub fails to boot Windows is another issue.

One thing's for sure, you're not going to get fresh eyes reviewing a 130+ post thread. I'd start a new one or post a question on askubuntu with all relevant information, if you haven't already found a similar case out there on the Net with suitable workarounds. The nice thing about askubuntu is that you can edit your question so all the relevant information is in a single post, up to date, tidy and readable.

---

### Post by mmcl26554 on 2013-10-23
Thanks I'll work on it.   FYI, the computer is a Gateway One (all in one computer GZ1220) the MB is intel and the only external cards are wireless and graphics.   I did a goole search for any post regarding Ubuntu installs on any version of this computer but didn't find much.  Again thanks for the good advice and I will work on it with that in mind.
Michael

---

### Post by John Jason Jordan on 2013-12-15
Searching the forums I found this thread, so I hope there are people here who can help, especially using Clonezilla to duplicate boot partitions.

I bought a new 17" System76 laptop with a 1 TB hybrid drive. I installed Xubuntu in a 100 GB partition and ~/ in a 300 GB partition, leaving the rest free space (no swap). At the time I ordered the computer I also ordered a 480 GB mSATA drive, intending to clone the two partitions on the 1 TB drive to it, then reformat the 1 TB drive for random data.

I installed the 480 GB mSATA drive and used gparted to create a 100 GB partition (SDB1) and used the rest for another partition (SDB2), and then I used a live CD of Clonezilla to clone the partitions on the 1 TB drive (SDA1 and SDA2) to the mSATA drive (SDB1 and SDB2). Clonezilla worked without errors, and the clone of SDA2 to SDB2 appears to be fine, but the clone of SDA1 to SDB1 failed to create a bootable image. That is, the computer still boots fine to SDA1, but will not boot to SDB1. If I boot to SDA1 Xubuntu comes up normally and I can mount both the partitions on the mSATA drive and all the files appear to be there, although, of course, viewing the files does not tell me if the partition is bootable. 

Having booted to SDA1 I used Gparted to set the flag on SDB1 as bootable, but it made no difference. 

I can easily use Clonezilla to recreate the clone of SDA1 to SDB1, but that would be pointless until I figure out what I did wrong to make it fail to make SDB1 bootable. Can anyone give me some pointers here?

---

### Post by oldfred on 2013-12-15
You cannot easily clone an image to another drive and keep both drives mounted. Full image backup is to restore to same drive or clone to a new drive when old drive is disconnected.

       Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

   
Files that may need update on image copy
 fstab, reinstall grub and grub's reinstall location. and change UUIDs first.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
If different computer:
/etc/hostname and /etc/hosts,

    
to see UUIDs
 sudo blkid -c /dev/null -o list

      
 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by John Jason Jordan on 2013-12-16
> **oldfred said:**
> You cannot easily clone an image to another drive and keep both drives mounted. Full image backup is to restore to same drive or clone to a new drive when old drive is disconnected.
       Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

Thank you for the prompt reply.

Let me point out that the old drive (sda) is 1 TB total. It has a boot partition with Xubuntu (SDA1) of 100 GB and a second partition for home of 300 GB (SDA2). These are the only partitions on the disk; the remainder of the disk is free space. The new disk is 480 GB and I have created a 100 GB partition to be the boot partition and a 380 GB partition for home. Note that the old drive is 1 TB and the new one is 480 GB, so I cannot do a disk to disk copy. I am limited to partition to partition cloning.

These disks are on a new computer, so the installation of Xubuntu on the old disk is only a couple weeks old. However, it took me five solid days to get all the programs and configurations the same as they were on my old computer. I have a lot of custom applications and configurations that are not trivial to get working. So let us please forget about a fresh install. 

The cloning with Clonezilla worked fine. I checked /etc/fstab on the clone and it is the same, so as long as I can boot to the new disk all should be fine.

I considered the suggestion to use:

    ```
sudo dpkg-reconfigure grub-pc
```

But that must be run from the booted partition, and I cannot boot to the new drive. 

Looking at the first few bytes of the new drive and the old drive, there are differences, which explains why the new drive is not bootable. 

According to everything I read about Clonezilla it is supposed to clone the partition so the clone will be bootable if the source was bootable. But it didn't do it for me. I probably did something wrong in the menus when I ran Clonezilla. Unfortunately, the documentation for Clonezilla seems to be sparse.

---

### Post by oldfred on 2013-12-16
You are going to have to change UUID and settings in fstab. Then reinstall grub to MBR of new drive manually or with Boot-Repair. Since grub remembers the drive to reinstall into you only need to run the dpkg reinstall to reset that drive setting after you get it working.

---

### Post by John Jason Jordan on 2013-12-16
> **oldfred said:**
> You are going to have to change UUID and settings in fstab. Then reinstall grub to MBR of new drive manually or with Boot-Repair. Since grub remembers the drive to reinstall into you only need to run the dpkg reinstall to reset that drive setting after you get it working.

SDA1 and SDB1 have the same UUID, and SDA2 and SDB2 have the same UUID.

sudo blkid
/dev/sda1: UUID="0c9621bb-ec81-43f3-85c5-16c3d12d500a" TYPE="ext4" 
/dev/sda2: LABEL="Home" UUID="2cdd7cc1-03f6-4f98-87a4-cd11ac08c617" TYPE="ext4" 
/dev/sdb1: UUID="0c9621bb-ec81-43f3-85c5-16c3d12d500a" TYPE="ext4" 
/dev/sdb2: LABEL="Home" UUID="2cdd7cc1-03f6-4f98-87a4-cd11ac08c617" TYPE="ext4" 

Do I need to change the UUID of these drives? Which one(s)? And the /etc/fstab files on SDA1 and SDB1 are identical. Also /boot/grub/grub.cfg is identical on both drives. 

From another thread I found instructions to use "sudo grub-install" so I did "sudo grub-install /dev/sdb," but, of course, to run it I was booted to SDA. After running the command I can select the new drive in the BIOS during boot and the computer will boot (previously it would just hang), but it still boots to SDA1. I would like to try booting to SDB1 without SDA present to see what would happen, but SDA is mounted under the keyboard so it's not trivial to remove it.

---

### Post by oldfred on 2013-12-17
See post #25.
It does not matter which drive you change, but you must be consistent that UUID matches fstab and grub and change both partitions so there are no duplicates.
You can get grub to boot even with wrong UUID in grub menu manually after you have changed UUID and fstab.

At grub menu use e for edit and change UUID in boot stanza to correct new entry or go to grub terminal and manually boot. Or you can edit out any references to UUID and use the old device like the manual boot example below.

From grub terminal, by exiting grub menu.
This would boot sda1, if that is what you want. 
 set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

Once you boot into your install then run sudo update-grub and all the UUIDs thru out the menu will be updated.

---

### Post by John Jason Jordan on 2013-12-19
OK, I think I finally understand out how to do it:

1) Use Clonezilla to clone SDA1 to SDB1 and SDA2 to SDB2.
2) Boot to a rescue CD or just to SDA1, because SDB1 won't be bootable yet. Run sudo update-grub.
3) Use tune2fs to generate new random UUIDs for SDB1 and SDB2
4) Run sudo grub-install /dev/sdb
5) Edit fstab on /dev/sdb1 so that it knows the correct new UUIDs of SDB1 and SDB2.

At this point I should be able to boot to SDB1. 

HOWEVER:

There is a huge problem now with Clonezilla. Note that I already used Clonezilla several days ago to clone SDA1 and SDA2 (home) to SDB1 and SDB2. For several days now I am still booting only to SDA, and there have been many changes. So I decided to use Clonezilla to repeat the cloning, replacing SDB1 and SDB2 with current clones of SDA1 and SDB2 before proceeding to use the above to make SDB bootable. But Clonezilla now fails with an error message "failed to clone ..." I see no messages as to why it failed. After Clonezilla failed I used Gparted to delete SDB1 and recreate it, but Clonezilla still fails.

The documentation on Clonezilla barely explains how to use it, and I haven't found a single word about what to do when things go wrong. Does anyone here know what might have happened?

---

### Post by oldfred on 2013-12-19
You can only run sudo update-grub in the booted install not from another install unless you chroot into the other install.
If you change UUIDs and update fstab, then you can manually install grub or use Boot-Repair. With Boot-Repair you can easily run a full uninstall/reinstall of grub with a mini-chroot and that would then update all of grub to new UUIDs.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

