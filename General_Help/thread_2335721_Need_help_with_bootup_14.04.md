---
title: "Need help with bootup 14.04"
date: 2016-08-31
forum: General Help
---

### Post by aviator1 on 2016-08-31
Hello Everyone.

Last month, I experienced a situation where my computer would not boot. I finally was able to run a boot repair program, which enabled me to get somewhat back to normal.

My situation now is this. I have 3 drives installed, my primary is a dual boot, SSD with Windows 7/Ubuntu 14.04. My back up is a 2 TB HDD storage disk. During my other issues, I plugged in a 500GB HDD, which has 12.04 on it. It i still installed.

As of now, I can boot up to my primary, and can access the other disks.

I tried disconnecting the 500 GB drive, and the system will not boot. It takes me to a grub repair message and is locked.

The same happens if I disconnect the 2 TB drive.

My goal is to get back to just my primary SSD and my 2 TB HDD storage.

I'm a long time user of Ubuntu, but not very fluent in the steps and commands, which may be required to solve these issues.

Thanks for any help.

Dave

---

### Post by Jimysbil on 2016-08-31
As I can see you have one grub for both of your Hard Disks.I assume they have both MBR (not GPT) because as I can see your Grub is probably installed on the MBR of your SSD but its files are installed on your 500GB (or at least they are getting load from there).
So my question is if you connect your 500 GB by itself will it boot with grub??

A possible fix is to connect your 500GB Hard Disk and reinstall grub and MBR on your current Hard Disk.

Let's suppose your First Disk is /dev/sda.
Open a terminal and type:
```
sudo su
```
in order to get root privileges.
Then type:
```
grub-install --boot-directory=/boot /dev/sda
```
This command should reinstall grub on the same hard disk you are running your OS.
Also type:
```
update-grub
```
to regenerate your grub configuration file.

But before you do anything type this command in your terminal and copy-paste the results here:
```
fdisk -l
```

---

### Post by aviator1 on 2016-08-31
fdisk -l does nothing. Just brings me back to the prompt.

I will try to see if it boots with just the 500 GB disk.

I cannot get to it until Thursday afternoon/evening.

Thanks for your help.

---

### Post by Jimysbil on 2016-09-01
In order to run the command 'fdisk -l' you should have root privileges.
Open the terminal and type:
```
sudo su
fdisk -l
```
It could also help you the command:
```
blkid
```

---

### Post by aviator1 on 2016-09-01
Here is the info fdisk -l.
```
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1cff2565

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     1023999      510976    7  HPFS/NTFS/exFAT
/dev/sda2   *     1024000   250569727   124772864    7  HPFS/NTFS/exFAT
/dev/sda3       250570750   500117503   124773377    5  Extended
/dev/sda5       466767872   500117503    16674816   82  Linux swap / Solaris
/dev/sda6       250570752   466767871   108098560   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x482840f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   488283297   244140625   83  Linux
/dev/sdb2       488284158   976771071   244243457    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5       488284160   976771071   244243456   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x67530d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *      206848   976768064   488280608+   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 1000.2 GB, 1000170586112 bytes
256 heads, 63 sectors/track, 121122 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16f2a91f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  4294967295  2147483647+  ee  GPT
```

More Info

```
Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x67530d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *      206848   976768064   488280608+   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 1000.2 GB, 1000170586112 bytes
256 heads, 63 sectors/track, 121122 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16f2a91f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  4294967295  2147483647+  ee  GPT
root@dave-desktop:/home/dave# blkid
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb1: UUID="a9182864-8c2c-4b72-ab5f-7db60ff4a922" TYPE="ext2" 
/dev/sdb5: UUID="b9a3dbe2-2969-4612-a8de-ea2c285f956a" TYPE="ext2" 
/dev/sdc2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdc3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdc5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdc6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
/dev/sde1: LABEL="TOSHIBA EXT" UUID="B27C47DA7C47984D" TYPE="ntfs" 
/dev/sdf1: LABEL="2TB External" UUID="6918d689-ad65-4f23-b158-11ed482769e3" TYPE="ext4" 
root@dave-desktop:/home/dave# blkid
/dev/sda1: LABEL="System" UUID="BC20303E202FFDC8" TYPE="ntfs" 
/dev/sda2: LABEL="OSDisk" UUID="E01A44131A43E4DE" TYPE="ntfs" 
/dev/sda5: UUID="80d61814-fc43-4c38-b772-d32945f6b4a1" TYPE="swap" 
/dev/sda6: UUID="75e89545-dc5c-4553-907d-23269bb7b2a9" TYPE="ext4" 
/dev/sdb1: UUID="a9182864-8c2c-4b72-ab5f-7db60ff4a922" TYPE="ext2" 
/dev/sdb5: UUID="b9a3dbe2-2969-4612-a8de-ea2c285f956a" TYPE="ext2" 
/dev/sdc2: UUID="01a0c8e9-208b-446f-8194-25189c603de1" TYPE="ext4" 
/dev/sdc3: UUID="4958eedc-3298-45c0-83f3-c4e4d20e4194" TYPE="swap" 
/dev/sdc5: UUID="e35ca651-476f-4313-a744-c5021cade941" TYPE="ext4" 
/dev/sdc6: UUID="6401838b-4d19-4e12-88fa-a944c9326ef9" TYPE="swap" 
/dev/sde1: LABEL="TOSHIBA EXT" UUID="B27C47DA7C47984D" TYPE="ntfs" 
/dev/sdf1: LABEL="2TB External" UUID="6918d689-ad65-4f23-b158-11ed482769e3" TYPE="ext4" 
root@dave-desktop:/home/dave# 
```

---

### Post by Jimysbil on 2016-09-01
As I can see from the prints /dev/sda is your Dual boot SSD and you are probably booted on your Ubuntu 14.04.
So the solution I would prefer should be to have for both of my disks a separated Grub as long as you have an OS on each one.
Use those commands in order to fix Grub for your SSD:
```
sudo su
grub-install --boot-directory=/boot /dev/sda
update-grub
```

* On the printed results it seems you have one 1TB and two 500GB Hard Disks connected so I guess the disk with Ubuntu 12.04 is /dev/sdb (not /dev/sde).I also guess the partition you have it installed is /dev/sdb1 because it has the boot flag enabled.
According to this you can install Grub in your external Hard Disk too by using the commands (with root privileges):
```
cd /
umount -f /dev/sdb1
mkdir -p /mnt/mnt
mount -t ext2 /dev/sdb1 /mnt/mnt
grub-install --boot-directory=/mnt/mnt/boot /dev/sdb
grub-mkconfig -o /mnt/mnt/boot/grub/grub.cfg
```

---

### Post by KitchM on 2016-09-01
> **aviator1 said:**
> I finally was able to run a boot repair program, which enabled me to get somewhat back to normal.

I am curious; what exactly did you do here?  What program and how did you use it.

---

### Post by aviator1 on 2016-09-01
Here is what I used
```
sudo **apt-add**-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```

There are not 2 500GB disks. There is a 1 TB dish, which is divided roughly into 2 500 GB partitions. The extra disk is a 500 GB disk, which appears to be divided into 2 each 250 GB disks.

I would like to get back to my original setup, which is the dual boot SSD and the 1 TB as a back up.

I would like to remove completely the 500 GB disk.

Thanks for your help.

---

### Post by Jimysbil on 2016-09-01
> **aviator1 said:**
> There are not 2 500GB disks. There is a 1 TB dish, which is divided roughly into 2 500 GB partitions. The extra disk is a 500 GB disk, which appears to be divided into 2 each 250 GB disks.

I would like to get back to my original setup, which is the dual boot SSD and the 1 TB as a back up.

I would like to remove completely the 500 GB disk.

Thanks for your help.

According to what your 'fdisk -l' command prints /dev/sda , /dev/sdb and /dev/sde have msdos partition table.
/dev/sda --> 256GB SSD (Dual Boot --> 2 NTFS , 1 swap , 1 ext4)
/dev/sdb --> 500GB HDD (Ubuntu 12.04 --> 2 ext2 partitions)
/dev/sde --> 500GB HDD (1 NTFS partition --> TOSHIBA EXT)

But it seems /dev/sdc and /dev/sdf have GUID partition table.
/dev/sdc --> 2TB (2 swap , 2 ext4 partitions)
/dev/sdf --> 1TB (One partition --> 2TB External??? this is not right)

I have already told you the solution to reinstall Grub on your SSD.But what is the problem with your 1TB Hard Disk??
In your original post never mentioned the 1TB Hard Disk.
I don't exactly understand the situation here.

You can also try
```
gdisk -l
```
* This command should print you details for disks with GUID partition table.

---

### Post by aviator1 on 2016-09-01
Jimysbil.

That worked. I disconnected the 500GB drive and can boot to Windows 7, or 14.04 on the SSD.

There are 2 other 14.04 selection possibilities, but they just seem to go in a circle. I get to a desktop and enter my password for the 1 TB drive. It tries to boot, but just returns to the desktop.

I also see an error message on the desktop, but it does not seem to do anything.

Overall, I am operational. It would be nice to be able to boot to the 1 TB drive, but not necassary.

I really appreciate your help.

---

### Post by Jimysbil on 2016-09-01
> **aviator1 said:**
> There are 2 other 14.04 selection possibilities, but they just seem to go in a circle.


Do you mean you have 2 more entries on your Grub for a second installation of Ubuntu 14.04 or for the same one you have on your SSD??

> **aviator1 said:**
> ...I get to a desktop and enter my password for the 1 TB drive. It tries to boot, but just returns to the desktop.


What do you mean it tries to boot??
Do you mean it is trying to mount??

As I can understand you are running an Ubuntu 14.04 and you can see your GUI.So you are trying to mount your drive and it asking you for your password in order to take root privileges.If your Hard Disk is not getting mounted is probably corrupted.

According to the prints of the command blkid your 1TB Hard Disk is /dev/sdf1 and it's type is ext4.
So if it's corrupted you could try those commands in order to fix it:
```
sudo su
fsck.ext4 -v /dev/sdf1
```

If this command does not work for you or it gives you some error try this:
```
mke2fs -n /dev/sdf1

```
This command should print you some (Superblock) numbers.
Then run the command:
```
e2fsck -b {one of your printed block numbers} /dev/sdf1
reboot
```
* If this doesn't work just try an other number.

---

### Post by aviator1 on 2016-09-01
Sorry, I don't understand some of your questions. Let me explain further.

When I turn on the computer, I get to a screen that allows me to make a selection as to where to boot.

As of now, the top selection is 14.04 on my SSD. That's great.

There are also selections for memory tests, and for Windows 7. Those all work(boot) properly.

There are 2 more selections which read for 14.04. If I select either one of those, it looks like it attempts to boot to the 1 TB drive and ends up at a desktop asking for my password.

Upon entering the password, it looks like it goes through some motions and returns to the screen requesting the password. Along this time, there is an error message at the top of the desktop, but seems to do nothing.

When I boot to my SSD, I can see and access all disks.

Thanks for your help.

Thanks for your help.

I really appreciate all the help, but I am a user, not a technical Ubuntu type.

I do not understand the following. 

"I have already told you the solution to reinstall Grub on your SSD.But what is the problem with your 1TB Hard Disk??
In your original post never mentioned the 1TB Hard Disk.
I don't exactly understand the situation here."

I have no idea how to reinstall Grub.

Thanks for your help.

---

### Post by KitchM on 2016-09-01
Yes, I do see where you did mention the 1 TB hard drive in your first post.  Maybe Jimsbil missed that.

However, you do need to be clear about something very important.  If I understand correctly, you are stating that you have a GRUB menu that has 5 items.  All is good until you mention those last two:
1. Did you mean to say that the 4th one takes you to a Ubuntu desktop, or did you mean that the request for password comes somewhere along in the boot-up process.
2. What does the fifth item do?

---

### Post by aviator1 on 2016-09-01
Can you tell me how to copy the grub menu?

---

### Post by Jimysbil on 2016-09-01
> **aviator1 said:**
> I really appreciate all the help, but I am a user, not a technical Ubuntu type.

I do not understand the following. 

"I have already told you the solution to reinstall Grub on your SSD.But what is the problem with your 1TB Hard Disk??
In your original post never mentioned the 1TB Hard Disk.
I don't exactly understand the situation here."

I have no idea how to reinstall Grub.

Thanks for your help.

I mean in your first post you said you had a 256GB SSD , a 2TB HDD and a 500GB HDD.You never mentioned something about 1TB HDD.

As for the Grub reinstallation you have probably succeed as long as your SSD is working again.

---

### Post by aviator1 on 2016-09-01
I apologize. I meant to say 1 TB hard drive.

I may have had an external drive plugged in at the time.

I really apologize for my misstatements.

I have a 256GB SSD, and a 1 TB HDD installed permanently.

I appreciate all your assistance.

All are working fine, just curious about the extra selections in the grub menu.



> **Jimysbil said:**
> I mean in your first post you said you had a 256GB SSD , a 2TB HDD and a 500GB HDD.You never mentioned something about 1TB HDD.

As for the Grub reinstallation you have probably succeed as long as your SSD is working again.

Again, I apologize. I am truly embarrassed. I posted before reviewing all the components.

My permanent drives are a 256GB SSD and a 2 TB HDD. The 2 TB is roughly partitioned into 2 1 TB partitions. The 2 TB may have 12.04 on it. The temporary 500 GB may have 12.04 on it. Don't know how to tell.

I had the 500GB drive temporarily installed (gone now) and it showed as 2 250GB drives (do not Know why)

I have 2 external drives, which I was using to do backups in case I messed something up while working here. One is a 500GB and the other is a 1 TB. They are gone now.

I can't apologize enough. You guys have been very gracious in extending your knowledge to me, and I did not give you the correct parameters at times.

I can boot up normally. My only concern is what the extra selections int he grub menu are for.

I do not know how to make a copy of the grub menu.

I sincerely thank you all for your help.

Regards.

---

### Post by Jimysbil on 2016-09-01
You can easily copy your grub configuration file.
Just type in a terminal:
```
gedit /boot/grub/grub.cfg
```
and copy-paste everything here.
You should have:
1 normal option to start ubuntu.
1 'Advanced options' submenu.
2 memtest options.
and 1 option for windows.

The 'Advanced options...' menu have multiple ways to start your OS and it could have startup options for older kernels.
The memtest options are for hardware check (Ram).

---

### Post by aviator1 on 2016-09-02
Here is what I get when I try to post the info from 
gedit /boot/grub/grub.cfg It is a very lengthy document. 


"Your submission could not be processed because a security token was missing.

If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php") and describe the action you performed before you received this error.
             
             Ubuntu Forums"

---

### Post by Jimysbil on 2016-09-02
If you can't copy-paste the content of grub.cfg you should be able to upload it as an attachment.
The contect is probably too big to copy-paste it here or it could make some confliction.

---

### Post by KitchM on 2016-09-02
Yes, sorry Jymsbil, I meant that the 1 TB drive was mentioned in a later post.  My bad.

Aviator1, I too am curious about the menu entries, and particularly the last two entries and what you meant by what you said about them.

---

### Post by aviator1 on 2016-09-02
> **Jimysbil said:**
> If you can't copy-paste the content of grub.cfg you should be able to upload it as an attachment.
The contect is probably too big to copy-paste it here or it could make some confliction.

Trying to add as an attachment, but can't seem to get it done. Can you give some directions. I get it uploaded, but can't seem to drag and drop.

---

### Post by aviator1 on 2016-09-04
Here is what I see when I boot up

Ubuntu
Advanced Options
Memory Test
Memory Test
Windows 7 Loader SDA1
Windows 7 Loader SDA2
14.04.04 SBD1
Advanced Options
14.04.04 SDC2
Advanced Options

---

### Post by Jimysbil on 2016-09-04
> **aviator1 said:**
> Here is what I see when I boot up

Ubuntu
Advanced Options
Memory Test
Memory Test
Windows 7 Loader SDA1
Windows 7 Loader SDA2
14.04.04 SBD1
Advanced Options
14.04.04 SDC2
Advanced Options

14.04.04 SBD1 --> You probably mean SDB1

This means you have installed ubuntu 14.04 on 2 more hard disks.The os-prober script of your grub scripts is getting used in order to find other oparating systems (except the one who's creating the grub configuration).
So if you disconnect those hard disks and execute the command 'update-grub' you will probably get rid of those extra entries (with their 'advanced options').

But because the most of times this is an annoying feature you can disable it (for every grub script) by adding a line in /etc/default/grub file so it won't be able to find an OS (or more) on the partitions you will choose.
Type the commands:
```
sudo su
gedit /etc/default/grub
```
and add a line like this:
```
GRUB_OS_PROBER_SKIP_LIST="[COLOR="#FF8C00"]{partition UUID}[/COLOR]@/dev/sd[COLOR="#FF0000"]XX[/COLOR]"
```

Example:
```
GRUB_OS_PROBER_SKIP_LIST="6a075169-2abe-4bfa-8021-9c34a4f981d2@/dev/sda1"
```

* After that type the command:
```
update-grub
```

---

### Post by Jimysbil on 2016-09-04
If the output of the command 'blkid' is steel the same for every one of your disks the line you should add to your /etc/default/grub file would be like this:
```
GRUB_OS_PROBER_SKIP_LIST="a9182864-8c2c-4b72-ab5f-7db60ff4a922@/dev/sdb1 / 01a0c8e9-208b-446f-8194-25189c603de1@/dev/sdc2"
```

---

### Post by aviator1 on 2016-09-04
At this time, there are only 2 HD in the computer. The 256 GB SSD and the 2 TB HDD. There are no external drives attached.

Where would I find the  "partition UUID" information and what sdXX would I use?

Thanks for your help, but I just do not understand some of the technical jargon.

---

### Post by Geoffrey_Arndt on 2016-09-04
1.    cd /dev/disk/by-uuid

then

2.    ll     (lower case el-el) (to display the uuid's)

3.    lsblk     (to see sdxx labels of drives & partitions)

---

### Post by aviator1 on 2016-09-05
Here's what I get when I try to reply with the info.

[h=1]Forbidden[/h] You don't have permission to access /newreply.php on this server.

---

### Post by oldfred on 2016-09-09
Your Forbidden error is a Forum hiccup. I have also gotten it several times and it still is not resolved as far as I know. Just try again later.

Rather than post various commands, often better & easier just to run Boot-Repair's Summary Report and post just the link it provides. That runs many standard commands plus some more complex commands to output some normally hidden info.

---

### Post by aviator1 on 2016-09-09
> **oldfred said:**
> Your Forbidden error is a Forum hiccup. I have also gotten it several times and it still is not resolved as far as I know. Just try again later.

Rather than post various commands, often better & easier just to run Boot-Repair's Summary Report and post just the link it provides. That runs many standard commands plus some more complex commands to output some normally hidden info.
I followed the instructions in the link you provided, but the info is very long, and I got another error message when I tried to post.

UPDATE:  Maybe this will work. [http://paste.ubuntu.com/23154349/](http://paste.ubuntu.com/23154349/)

---

### Post by oldfred on 2016-09-09
You have Windows in sda with BIOS/MBR and grub installed to MBR booting 14.04 sda6.
You have Ubuntu in sdb on a BIOS/gpt drive. It looks like you had an old bios_grub as sdb1, but now bios_grub is sdb4. With gpt partitioning you must have a bios_grub for BIOS boot with grub.
You show two installs, 14.04 in sdb2 and an old 10.04. I do not think 10.04 would have worked from gpt, but I think I started using BIOS/gpt with 10.10.

Which install of 14.04 is your main working install?
I would suggest keeping Windows boot loader in sda's MBR so you can directly boot it, and only have grub in gpt's protective MBR on sdb to boot an install on sdb. Then set BIOS to boot sdb and use grub to choose to boot Ubuntu or Windows. Grub only boots working Windows and you may then be able to directly boot Windows from UEFI/BIOS or may still need the Windows repair flash drive when Windows needs fixes.

---

### Post by aviator1 on 2016-09-09
> **oldfred said:**
> You have Windows in sda with BIOS/MBR and grub installed to MBR booting 14.04 sda6.
You have Ubuntu in sdb on a BIOS/gpt drive. It looks like you had an old bios_grub as sdb1, but now bios_grub is sdb4. With gpt partitioning you must have a bios_grub for BIOS boot with grub.
You show two installs, 14.04 in sdb2 and an old 10.04. I do not think 10.04 would have worked from gpt, but I think I started using BIOS/gpt with 10.10.

Which install of 14.04 is your main working install?
I would suggest keeping Windows boot loader in sda's MBR so you can directly boot it, and only have grub in gpt's protective MBR on sdb to boot an install on sdb. Then set BIOS to boot sdb and use grub to choose to boot Ubuntu or Windows. Grub only boots working Windows and you may then be able to directly boot Windows from UEFI/BIOS or may still need the Windows repair flash drive when Windows needs fixes.

The 256GB SSD has 14.04 and Windows 7 on it. Both are booting fine. When I get to the selection screen, if I do nothing, it boots correctly to the 14.04. I can select Windows 7 or the memory tests with no problems.

If I scroll down to the other 2 14.04 selections, it just goes to a desktop screen, requests a password, and returns to the desktop screen where it asks for a password again.

Ideally, I would like to replace the 2 TB HDD with the 500 GB, as I have a use for the larger drive in my home surveillance gear. However, I don't want to take the chance of messing all this up.

Other than the 2 extra selections, it's working fine.

Thanks for your help. I will read the link you provided above. I just do not understand the technical terms or methods.

---

### Post by oldfred on 2016-09-09
You may want to houseclean older kernels, you have a lot. With 16.04 it now keeps only 2 by default.
       [URL="https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels"]https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels
[/URL]
 #Current kernel:
uname -a 
      
 I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu) 
    
Your grub menus also show a sdc install?

For your install in sdb, grub shows booting from hd0 which will not work. If you get to grub menu, you may be able to manually edit entry from hd0,2 to hd1,2.
This may also just update grub in install in sda, to correct drive.
sudo update-grub

When you have multiple installs, best to regularly use Boot-Repair just to know what is where. Especially if moving drives around.

I prefer to let main working install control booting, but then turn off os-prober and manually add my own boot entries to boot a partition.
       
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by aviator1 on 2016-09-09
> **oldfred said:**
> You may want to houseclean older kernels, you have a lot. With 16.04 it now keeps only 2 by default.
       [URL="https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels"]https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels
[/URL]
 #Current kernel:
uname -a 
      
 I prefer synatic and keeping 2 kernels, current and one known working older on.
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu) 
    
Your grub menus also show a sdc install?

For your install in sdb, grub shows booting from hd0 which will not work. If you get to grub menu, you may be able to manually edit entry from hd0,2 to hd1,2.
This may also just update grub in install in sda, to correct drive.
sudo update-grub

When you have multiple installs, best to regularly use Boot-Repair just to know what is where. Especially if moving drives around.

I prefer to let main working install control booting, but then turn off os-prober and manually add my own boot entries to boot a partition.
       
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Oldfred, I appreciate you Brother, but I do not understand much of what you said......I really do appreciate your effort to help me, but I'm just not very far along in understanding terms and actions. I've been using for a long time, but haven't gotten into the inner workings very much.

I will have a look at the links you have provided.

Do you think an upgrade to 16.04 would help?

Hope your trip to the wedding went well.

---

### Post by oldfred on 2016-09-09
We can go step by step on issues if you want.
If you have AMD video, I would not yet upgrade to 16.04, otherwise it may be better.

Wedding went well. :)

---

### Post by aviator1 on 2016-09-09
> **oldfred said:**
> We can go step by step on issues if you want.
If you have AMD video, I would not yet upgrade to 16.04, otherwise it may be better.

Wedding went well. :)

I ran "sudo apt-get autoremove --purge" and the last 14.04 selection was removed. I also ran GRUB repair, but nothing seemed to change.

If I select that last 14.04 at boot up, it takes me to a desktop, asks for a password, and returns me to the desktop again. The only password it will accept is the one I had on the 2 TB drive.

I use a different PW for the 256 GB SSD.

I have an NVidia GT 640 video card. Not sure if I have anything with AMD for video.

As of now, everything seems to be working fine. If you think it would be a good idea to further clean up the boot up/hard drive issues, then I would be pleased to follow step by step instructions.

However, I know you must be assisting other people who may have more of a need than I do right now.

I do appreciate your help.

Regards.

---

### Post by oldfred on 2016-09-09
I prefer synaptic as then you can see each kernel, but the full purge will totally houseclean old kernels.

 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a 
      
 I prefer synatic and keeping 2 kernels, current and one known working older on.
 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) 

Other ways:
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

### Post by aviator1 on 2016-09-11
> **oldfred said:**
> I prefer synaptic as then you can see each kernel, but the full purge will totally houseclean old kernels.

 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a 
      
 I prefer synatic and keeping 2 kernels, current and one known working older on.
 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) 

Other ways:
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

dave@dave-desktop:~$ uname -a 
Linux dave-desktop 3.13.0-95-generic #142-Ubuntu SMP Fri Aug 12 17:00:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
dave@dave-desktop:~$

---

### Post by oldfred on 2016-09-11
Now install synaptic:
sudo apt-get install synaptic

Then go into synaptic and in search box  look for linux-image.
Do not delete 3.13.0-95-generic #142-Ubuntu and generally best to keep one slightly older like -94 and delete/totally purge all the other much older ones.

---

### Post by aviator1 on 2016-09-11
> **oldfred said:**
> Now install synaptic:
sudo apt-get install synaptic

Then go into synaptic and in search box  look for linux-image.
Do not delete 3.13.0-95-generic #142-Ubuntu and generally best to keep one slightly older like -94 and delete/totally purge all the other much older ones.

I will get to this tomorrow afternoon.

Are these good examples of what i should delete? Thanks for your help

Linux-signed-image 3.13.0-92-generic

Linux-signed-image 3.13.0-91-generic

Linux-signed-image 3.13.0-87-generic

---

### Post by oldfred on 2016-09-11
Yes,

You typically want to keep two. The one you are currently using of course and one older one that you used before. That might be -94, but if you had not updated regularly it may have skipped from -92 to your current -95. 
And then -91 and -87 for sure should be purged.

---

### Post by aviator1 on 2016-09-17
> **oldfred said:**
> Yes,

You typically want to keep two. The one you are currently using of course and one older one that you used before. That might be -94, but if you had not updated regularly it may have skipped from -92 to your current -95. 
And then -91 and -87 for sure should be purged.

Thanks. i will get started. I have been offline, and will be back on next week.

I appreciate your help.

---

