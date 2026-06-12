---
title: "[SOLVED] Nightmare... backup/restore strategy"
date: 2007-08-14
forum: General Help
---

### Post by mesh on 2007-08-14
First off thank you for anyhelp. 
Objective:  Restore my system as if i put in a new hard drive, repartitioned it and brought it back up. The reason being is this - every time i want to give linux a chance i get setup the way i want and thats great, but down the line something happenes and i have to reinstall and go through the task of getting it config'd the way i like so it just turns me off and away. Anyway below are the steps ive taken so far. I hope i have all the steps correct. Ive been trying to document all this.

-I first backed up my system with the following command:
  - tar -cvzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I then did the following to delete,create and format a new partition.
-booted into the live cd
-fdisk /dev/sda to go into the fdisk menu
-Type: p to get a list of partitions
-Tyep: d to delete a partition 
-in my case it was partition 1 (sda1)
--type: n to create a new partition
-type: w to write all the changes (a few prompts in between)
-I then formatted the newly crated partition with the following
  mkfs.ext3 /dev/sda1
-while still in the live cd i then created a directory /mnt/ubu
-i then mounted /dev/sda1 to /mnt/ubu
-extracted the contents of my backup archive to /mnt/ubu with the following
  -tar -xvpzf backup.tgz -C /mnt/ubu
-recreated the proc, sys, mnt directories
-restored grub by doing the following:
  	1. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.
	2. Type "grub" which makes a GRUB prompt appear.
	3. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use             whatever your computer 	spits out for the following lines. 
	4. Type "root (hd0,3)".
	5. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you                           want to write GRUB to 	the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)". ( I tried both) - 
	6. Type "quit".
	7. Restart the system. Remove the bootable CD. - NO SUCCESS

I then tried the following from the live cd:
	1.got a root shell
	2.made a /mnt/ubu folder
	3.i then mounted /dev/sda1 to /mnt/ubu
	4.chrooted /mnt/ubu
	5.grub-install /dev/sda
	6.exit and reboot - NO SUCCESS.

All attempts ended in me seeing the Ubuntu splash for a really long time with no bar movement and it eventuall kicked me to the busybox shell "/bin/sh: can't access tty; job contorl turned off" (initramfs).

**NOTE: The only way i can get my system back up is by doing this. Install ubuntu and without doing anything else back make a ghost image of the base install. then repartition, recreate, etc. slap the image onto my partition. after im done imaging i reboot once and login, make a back up of /boot/grub and /etc/fstab to a usb drive.I then boot to the live cd extract my backup same as above, and copy the back up of the /boot/grub and /etc/fstab to overwrite the ones in my backup. this will bring my system back up with all my settings. Maybe it has something to do with the UUID's? I grep'd uuid and theyre reference in different places so iim not sure if this will give me problems down the road**

Im sorry for the long post, but  i hope someone can learn from my mistakes. thanks again.

---

### Post by PentaxFollower on 2007-08-14
I've started to backup my Ubuntu for the same reason as you.
Have you tried using PartImage? It makes (optionaly compressed) image of selected partition and works fine for me. It's very easy to use - especcialy if run from bootable SystemRescueCd ([http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")).

---

### Post by mesh on 2007-08-14
> **PentaxFollower said:**
> I've started to backup my Ubuntu for the same reason as you.
Have you tried using PartImage? It makes (optionaly compressed) image of selected partition and works fine for me. It's very easy to use - especcialy if run from bootable SystemRescueCd ([http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")).

Thanks for the reply. Ill check it out. If it works for me ill use it, but id like a solution to the problem im having now. Im just trying to understand why my method isnt working. Im wondering if im going to have to use dd command. Anyone? Thanks again PentaxFollower. Peace

---

### Post by mesh on 2007-08-14
Would someone be so kind as to post there backup / restore methods?

---

### Post by capink on 2007-08-14
These steps I used to restore my system in the past.

To backup:

```
sudo tar cvzp --exclude=/proc/* --exclude=/lost+found/* --exclude=/tmp/* --exclude=/mnt/* --exclude=/sys/* --one-file-system -f /path/not/on/root/partition/backup.tgz /
```

To restore:

```
sudo tar xvzp --same-owner -f /path/to/backup.tgz -C /
```

Don't forget to use sudo to be able to backup and restore files readable only by root.


Edit: instead of excluding /proc we exclude /proc/* and so on with other dirs as well. This way we don't have to recreate these dirs at restore time.

Edit2: Using the option --one-file-system will exclude directories on partitions other than the root. If /home is on the same partition as root and you want to exclude it, don't forget to add the option --exclude=/home/* to the above command.

---

### Post by mesh on 2007-08-14
> **capink said:**
> These steps I used to restore my system in the past.

To backup:

```
sudo tar cvzp --exclude=/proc --exclude=/lost+found --exclude=/tmp --exclude=/mnt --exclude=/sys --one-file-system -f /path/not/on/root/partition/backup.tgz /
```

To restore:

```
sudo tar xvzp --same-owner -f /path/to/backup.tgz -C /
```

Don't forget to use sudo to be able to backup and restore files readable only by root.

Is this with a freshly created partition? and with no need to reinstall grub?

---

### Post by glennric on 2007-08-14
If you have booted the live CD why not use gparted to create the partitions.  It has a nice gui and makes this rather simple.  You will still need to install grub.  See [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")
for more details.

---

### Post by capink on 2007-08-14
No, you will still need to install grub form the live cd. Honestly, I saw nothing wrong with the steps you wrote above, that is how I successfully restored grub before, but it was to the master boot record (hd0).

One interesting thing is that you are repartitioning, and that would change the UUID of the boot partition. I think you have to get the new UUID to replace the old one in the /boot/grub/menu.lst. This maybe the  cause - I am not so sure - of your problem. To get the new UUID type:

```
ls -al /dev/disk/by-uuid/
```


Edit: Another command to get the UUIDs:

```
blkid
```

---

### Post by mesh on 2007-08-15
> **capink said:**
> No, you will still need to install grub form the live cd. Honestly, I saw nothing wrong with the steps you wrote above, that is how I successfully restored grub before, but it was to the master boot record (hd0).

One interesting thing is that you are repartitioning, and that would change the UUID of the boot partition. I think you have to get the new UUID to replace the old one in the /boot/grub/menu.lst. This maybe the  cause - I am not so sure - of your problem. To get the new UUID type:

```
ls -al /dev/disk/by-uuid/
```

Im mos def gonna try the uuid thing thanks mang. Ill report back. Like i said at the end of my post when i got it to work was when i backed up /etc/fstab (uuid ref) and /boot/grub (uuid ref in menu.lst) after i restored a ghost image i created to test that theory and it booted successfuly. Is there any way to generate a new uuid across the board? What i mean is create a new uuid and have it write to where ever its referenced. I grep'd uuid and its referenced in quite a few places. Anyway worse case i guess i can just manually make the changes. Thanks again. Peace.

---

### Post by capink on 2007-08-15
To avoid problems with UUID after formatting and repartitioning I use labels instead. I make it a habit to label my disks alphabetically: C, D, .... using the command e2label. And I replace any reference using UUID=....... with LABEL=...

Also note that you most probably need to change the UUID references in fstab as well.

---

### Post by mesh on 2007-08-15
Okay i finally got my system to boot after a repartition/restore. WHOOHOO!! 

Below is a quick guide if anyone has an opinion please post it. Im not sure if my solution will have any reprocutions down the road, but ive definitely made progress:

-Boot into the ubuntu live cd

-Open up a terminal

-type: umount /dev/sda1 to unmount the partition with the linux installation on it (might get an error, but thats ok)

-type: fdisk /dev/sda to go into the fdisk menu

-Type: p to get a list of partitions

-Tyep: d to delete a partition

-its going to ask you which partition select the appropriate one hit enter

-type: n to create a new partition

-its going to ask if you want it to be primary - type: p for primary

-Next just let it span from the first cylinder to the last (defauilt settings, just hit enter twice)

-If its going to be a fat32 partition type: t then answer b (skip this step if its going to be a native linux partition)

-keep the defualt linux type

-FINALLY type: w key to write the new partition

-to format to ext3 tyupe: mkfs.ext3 /dev/sda1 to format to a linux partition

-when the new partition is ready below is what i did next

-while still in the ubuntu live cd i mounted /dev/sda1 to /mnt/ubu (i first had to create the directory ubu under /mnt)

-I then extrated the contents for my backup.tgz to /mnt/ubu

-i then recreated the proc mnt and sys directories (they were excluded when i backed up my system)
   -ref:   [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

-I then restored the grub with the following: ref: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

	1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

	2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

	3. Type "grub" which makes a GRUB prompt appear.

	4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,0)". Use    whatever your compute spits out for the following lines. 

	5. Type "root (hd0,0)".

	6. Type "setup (hd0,0)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)". 

	7. Type "quit".

**BELOW IS WHAT MADE THE DIFFERENCE AND GOT MY RESTORE TO BOOT**

-I LOOKED AT MY UU-ID BYE TYPING ls -la /dev/disk/by-uuid

--I NOTICED THAT THE UUID LISTED ADN THE UUID IN MY MENU.LST DID NOT MATCH

--I EDITED MY MENU.LST AND I MANUALLY ENTERED THE UUID THAT WAS OUTPUTTED WHEN I TYPED ls -la /dev/dis/by-uuid

-REBOOTED. THE END.

Note: Please excuse me if this isnt up to ubuntu forums standards i just wanted to post this in hopes that it might help someone out. Again if i missed anything please post, if you have an opinion or if i made a mstake. Thanks to all for you help. Im going to try this again to make sure it woks. Peace

---

