---
title: "newbie questions..."
date: 2006-12-23
forum: General Help
---

### Post by hairmetal4ever on 2006-12-23
OK - have some questions now that I have Ubuntu installed.

First - I can't read my drives.  When I did the install, I chose the first option, the resize/dual boot option,  I have two hard drives, the main drive a 40 gig w/2 20 GB partitions, (in windows they are the C and E drives) one is the windows only partition and is NTFS. The other I intended as useable for both, it's currently empty and uses FAT32 (the "E" drive using windows terminology.)  Then I have a second drive, 80 GB that windows had as a single partition called the D Drive.  When I installed ubuntu I used that second hard drive, creating a 50 GB partition in that process.  I can't tell which partition is my new one and which is my old one, I click on them and they say "unable to mount selected volume."

I don't even care if I can't see the windows system partition from Ubuntu, there's nothing on there Linux can run anyway, any media files or documents I'll put in one of the FAT32 or the Linux native portion.  I have in my "Computer - File Browser" the following:

Floppy
DVD-ROM
DVD+RW
Canon i470D storage (my printer has a slot for an SD camera card)
"18.6 GB Volume (I assume this is my "C" drive in Windows and has the windows stuff on it)
"D Drive" which was the original name in windows of the second 80 GB drive
"Secondary Partition" which is the name for what was the "E" drive in WIndows
Then there is "Filesystem" which is the only one I can actually open or read.  The other ones, anything I try to do it says "unable to mount the selected volume."  Even the "Filesystem" drive isn't right, if I right-click properties it says size "unknown" as it does for the others.

Then, I try to set up my printer, and the system detects it but I can't seem to install it.

---

### Post by shane2peru on 2006-12-23
Ok, lets get you using the FAT32 partition first, and then we will worry about the printer.  You need to open a terminal **Applications - Accessories - Terminal**  then you can copy and paste this in the terminal:
```

sudo fdisk -l

```

This is going to show us all your hard drives and there partitions.  Paste the output here.

Next we need to take a look at your fstab - this is the file that is in charge of mounting your partitions.  In the terminal type or paste:
```
cat /etc/fstab
```  Please paste the output here.

Shane

---

### Post by hairmetal4ever on 2006-12-24
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS
/dev/hda2            2434        4865    19535040    f  W95 Ext'd (LBA)
/dev/hda5            2434        4865    19535008+   b  W95 FAT32

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5667    45520146    7  HPFS/NTFS
/dev/hdb2   *        5668        9640    31913122+  83  Linux
/dev/hdb3            9641        9733      747022+   5  Extended
/dev/hdb5            9641        9733      746991   82  Linux swap / Solaris




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
bryan@bryan-desktop:~$

---

### Post by shane2peru on 2006-12-24
Ok, in your fstab we are going to add a line that will allow you to see your FAT32 partition which in Linux terms is called hda5 

Ok, first we are going to open up the terminal again and type or paste this:```

sudo mkdir /media/fat32 
```  Where the fat32 is, you can use whatever name you want to call your partition.  I call mine storage.  I would avoid using capital letters and spaces in the name, it will confuse things.  If you use something other than fat32, just remember to replace fat32 with whatever you decided to use.

Next in the terminal type:```
gksu gedit /etc/fstab 
```  Be careful here as this contains all the data for mounting your other drives.  Toward the bottom you are going to cut this line and paste it into your fstab:
```
 /dev/hda5 /media/fat32       vfat    defaults,utf8,umask=007,gid=46 0       1
```  Notice that there is a fat32 in there if you used another name you will need to change that part.  Next we are going to put this into a terminal ```
sudo mount -a
```  Now you should be able to go to Places, and Click on your new fat32 partition, it should be listed there, also it should show up on your desktop with the name that you gave it or fat32.  We will need to check it and make sure that your settings are correct so that you can read and write to this partition.  Copy a file out of your /home folder and paste it into that new partition we created.  If you can write to it you should be set to go!  If you have any problems please post the output of ```
cat /etc/fstab
``` so we can see what you have.  We may need to change some of the numbers around in the line that I gave you.

Shane

---

### Post by hairmetal4ever on 2006-12-24
> **shane2peru said:**
> Ok, in your fstab we are going to add a line that will allow you to see your FAT32 partition which in Linux terms is called hda5 

Ok, first we are going to open up the terminal again and type or paste this:```

sudo mkdir /media/fat32 
```  Where the fat32 is, you can use whatever name you want to call your partition.  I call mine storage.  I would avoid using capital letters and spaces in the name, it will confuse things.  If you use something other than fat32, just remember to replace fat32 with whatever you decided to use.


OK.  Did that.  

> **shane2peru said:**
> Next in the terminal type:```
gksu gedit /etc/fstab 
```  Be careful here as this contains all the data for mounting your other drives.  Toward the bottom you are going to cut this line and paste it into your fstab:
```
 /dev/hda5 /media/fat32       vfat    defaults,utf8,umask=007,gid=46 0       1
```  Notice that there is a fat32 in there if you used another name you will need to change that part. 

OK, I did that, and I got this message in the terminal - "(gedit:5258): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
" but it still opened another window and I pasted that message and saved it.

> **shane2peru said:**
> Next we are going to put this into a terminal ```
sudo mount -a
```  Now you should be able to go to Places, and Click on your new fat32 partition, it should be listed there, also it should show up on your desktop with the name that you gave it or fat32.  We will need to check it and make sure that your settings are correct so that you can read and write to this partition.  Copy a file out of your /home folder and paste it into that new partition we created.  If you can write to it you should be set to go!  If you have any problems please post the output of ```
cat /etc/fstab
``` so we can see what you have.  We may need to change some of the numbers around in the line that I gave you.

Shane

Did that, and now it disappeared totally.  The results of the last command you had me enter:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5 /media/LNX       vfat    defaults,utf8,umask=007,gid=46 0       1
bryan@bryan-desktop:~$

---

### Post by shane2peru on 2006-12-24
> **hairmetal4ever said:**
> 
Did that, and now it disappeared totally.  The results of the last command you had me enter:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5 /media/LNX       vfat    defaults,utf8,umask=007,gid=46 0       1
bryan@bryan-desktop:~$
Ok, what disappeared totally?  Ok, that is good it is in your fstab.  On your desktop do you see any new icons for partitions?  Or is that what disappeared?  

Shane

---

### Post by hairmetal4ever on 2006-12-24
> **shane2peru said:**
> Ok, what disappeared totally?  Ok, that is good it is in your fstab.  On your desktop do you see any new icons for partitions?  Or is that what disappeared?  

Shane

The FAT32 drive at least showed up before under Places --> Computer.  It doesn't now and is also not on the desktop.  Do I need to reboot or something?

Did this message have something to do with it?

> - "(gedit:525: GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
.

---

### Post by shane2peru on 2006-12-24
No I don't think error message had anything to do with it, because you did get the line into the fstab.  Maybe try rebooting.  Edgy is sometimes a little funny about mounting, and sometimes mounts better on a reboot.  After you reboot and if it doesn't come up put this in a terminal:
```
sudo mount /dev/hda5 /media/LNX
```  If it doesn't like that command and gives you any errors post the output here.  If it doesn't give you any errors than it mounted and you are good to go.  If it says that it is already mounted then we will need to start playing with the numbers in your fstab, we can figure them out pretty simply.  There are several examples on the forums that I will dig up and we can work through it.

Shane

---

### Post by hairmetal4ever on 2006-12-24
OK - the drive shows up now and I can access it.  How about the rest?  And do I have to worry about losing data on the windows partitions if I mount them in Ubuntu?

---

### Post by shane2peru on 2006-12-24
Ok, were you able to paste a file to the new partition.  We need to establish that you have read write (rw) access to the drive.  If you can only read it without writing to it, we haven't succeeded yet.  If you can write to it then yes we are done with that partition.  As far as your windows Partition, I assume you are refering to your NTFS partition?  You really don't want to access that.  Really you cannot write to NTFS partitions.  However if you are interested, I can show you how to do that, so that in the rare event you want to go and get a file from there, you will be able to.  That would depend more on you.  Let me know.  Also you may want to start a new thread for your printer issue.  I guess I could have suggested that in the beginning and you could have been working on it.  Also when you post that thread, make the title something that someone will look at, Like:  **Getting my HP1310 Printer to work**  That way people will be more pron to open the thread and take a look at helping you out.  Just a suggestion to help you get help faster ;)  .  Let me know if you are able to save files to your new partition.  

Shane

---

### Post by fragos on 2006-12-24
I've found using gparted makes things much easier.  gparted can assign mount point without reformating and fstab is fixed for you.  In my case I have a couple of extra partitions.  /Share is used to share data between distros and /Other is a second distro.  You also need to run gparted in the other distro to to name and mount the partitions.  The names need not be the same for both distros.  Distro 1's / becomes distro 2's /Other.  Making Windows play nice with Linux -- it won't, I handled by not having Windows on my machines at all.

---

### Post by shane2peru on 2006-12-24
> **fragos said:**
> I've found using gparted makes things much easier.  gparted can assign mount point without reformating and fstab is fixed for you.  In my case I have a couple of extra partitions.  /Share is used to share data between distros and /Other is a second distro.  You also need to run gparted in the other distro to to name and mount the partitions.  The names need not be the same for both distros.  Distro 1's / becomes distro 2's /Other.  Making Windows play nice with Linux -- it won't, I handled by not having Windows on my machines at all.

Hey, thanks!!!  That is nice to know.  I will have to check that out.  That is a lot easier for newbies!  Especially since Edgy switched to using the numbers.  I know you can do it without the numbers, but I would be curious if using this method wrote the fstab with the number system.  

Shane

---

### Post by hairmetal4ever on 2006-12-24
Too much of a noob to understand those last two posts at all.

But it's letting me read-write to that partition.  However, I still can't completely use the "File System" partiion or my DVD drives!!

---

### Post by shane2peru on 2006-12-24
Yeah, you shouldn't be able to access your filesystem, that is where the system files are.  It is setup that way so that noobs and experienced users have less of a chance of messing things up.  There is really nothing in there that you need to access.  As far as your DVDrom, when you pop a CD in and push it in, wait a few seconds and it should auto mount.  If it doesn't we have an issue with that.  You may need to start new thread for that, because that is a bit out of my range.  I may be able to help you a little, but if we run into serious issues, I wouldn't be able to help you.  :D  I'm just a noob in stage 2.  ;)  I'm glad we got that partition running for you.

Shane

PS, how many of those DVD drives do you have anyway?  I noticed one is located in your fstab, so theoretically it should work.  Try inserting a disk in each one (one at a time of course)  and wait a few seconds to see if it auto mounts (which it should).

---

### Post by hairmetal4ever on 2006-12-24
[QUOTE=shane2peru;1927949]Yeah, you shouldn't be able to access your filesystem, that is where the system files are.  It is setup that way so that noobs and experienced users have less of a chance of messing things up.  There is really nothing in there that you need to access.  As far as your DVDrom, when you pop a CD in and push it in, wait a few seconds and it should auto mount.  If it doesn't we have an issue with that.  You may need to start new thread for that, because that is a bit out of my range.  I may be able to help you a little, but if we run into serious issues, I wouldn't be able to help you.  :D  I'm just a noob in stage 2.  ;)  I'm glad we got that partition running for you.

Shane

PS, how many of those DVD drives do you have anyway?  I noticed one is located in your fstab, so theoretically it should work.  Try inserting a disk in each one (one at a time of course)  and wait a few seconds to see if it auto mounts (which it should).  I have two of them.  A DVD-ROM and DVD+RW.  Just put a DVD movie in and it said "[Totem could not play 'dvd:///media/cdrom0" and under that "No URI handler implemented for "dvd"."

However, it can read the discs I put in it if they're not movies.

As far as the Filesystem, I don't even see how big it is.  I split my D drive into two HUGE partitions and I assume one is the Filesystem, and all that is wasted if I can't access it.  If it's not then it's gone.

---

### Post by shane2peru on 2006-12-24
> **hairmetal4ever said:**
>   I have two of them.  A DVD-ROM and DVD+RW.  Just put a DVD movie in and it said "[Totem could not play 'dvd:///media/cdrom0" and under that "No URI handler implemented for "dvd"."

However, it can read the discs I put in it if they're not movies.

As far as the Filesystem, I don't even see how big it is.  I split my D drive into two HUGE partitions and I assume one is the Filesystem, and all that is wasted if I can't access it.  If it's not then it's gone.

Ok, well, that is good, your DVDrom works!!!  That is a matter of configuration.  I don't remember if you said you are using Edgy or Dapper.  Anyway, [here]("http://easylinux.info/wiki/Ubuntu_Edgy") is some good documentation for Edgy.  And getting it to play DVD's.  You may be able to change your Filesystem disk size.  However that is a little risky.  You will definitely want to back up before attempting this operation.  Ok, here is your setup:

Disk /dev/hda: **40.0 GB**, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2433 19543041 7 HPFS/NTFS [COLOR="Red"]- your actuall Windows installation with NTFS - about 20GB[/COLOR]
/dev/hda2 2434 4865 19535040 f W95 Ext'd (LBA) - [COLOR="Red"]Extended partition[/COLOR]
/dev/hda5 2434 4865 19535008+ b W95 FAT32 - [COLOR="Red"]Your Fat Partition we just mounted! - about 20GB
[/COLOR]
Disk /dev/hdb: **80.0 GB**, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 5667 45520146 7 HPFS/NTFS - [COLOR="Red"]about 45GB dedicated to Windows with NTFS[/COLOR]
/dev/hdb2 * 5668 9640 31913122+ 83 Linux - [COLOR="Red"]about 32 GB for Your Linux distribution[/COLOR]
/dev/hdb3 9641 9733 747022+ 5 Extended - [COLOR="Red"]Extended partition[/COLOR]
/dev/hdb5 9641 9733 746991 82 Linux swap / Solaris - [COLOR="Red"] about 746MB for your swap space[/COLOR]

Ok, I'm assuming you are talking about the 80 hdd that you partitioned into 2 large partitions.  That is the second one down.  I explained your partitions in [COLOR="Red"]Red[/COLOR] to help you understand what you are looking at.  If I understand all this correctly you are fine, because your filesystem and your /home directory are sharing the same partition.  There fore you have lots of room for your /home directory.  You are setup good, and everything should work fine.  your filesystem is hidden but actually shares with your /home so if you can see how much free space you have on your home, that is the same amount you have on your filesystem.  You are good to go!

Shane

---

### Post by hairmetal4ever on 2006-12-25
How do I see what's in my /home directory?  And how big is it?  I'm still learning all this stuff.  Is this:

/dev/hdb2 * 5668 9640 31913122+ 83 Linux

the /home directory?

---

### Post by shane2peru on 2006-12-25
You /home directory is where all your personal settings are stored.  It is also a "My Documents" type directory, where you will/can store all your files music, Pictures, etc.  It is actually located at /home/your.user.name  So if you have more than one user there would be /home/user1  and a /home/user2  directory.  When you log in it automatically notes who is using the computer and where their directory is, therefore you are the only one allowed to modify files in your 'home' directory.  If we were in windows it would look like this:  C:/Home/UserName   - Just to give you an idea.  The filesystem is also referred to as the root directory and is always referred as this **/**  just a slash.  That is a basic explanation of the Linux file system.  Now, if you click on **Places - Home Folder**  It will open a file manager.  Do not click on any files or folders and at the very bottom of the window you will notice that it will tell you how much space you have free in your 'home' directory.  I think this is the default setup for Nautilus (the file manager that opens), but I have altered mine so much that I don't know if yours will automatically display this info or not.  If not you can click the little up arrow at the top of Nautilus, and this will show you the folder where your users folder is located.  You can right click on your username and select properties, and this will show you how much free space you have as well as how much space this folder takes up.  Also if you click on the up arrow one more time you will be at the 'filesystem' or the / .  You cannot modify these files as they are system files, you are allowed to look at them and browse through them and see what is there.  You can modify them, but you must be root, and it is not reccommended unless you know what you are doing.  Matter of fact we edited them when we edited /etc/fstab - remember this line?  If you are still in Nautilus, you will see a folder called etc, if you double click it you will notice that there are many files in there and one of those files will be a file/text document called fstab.  You will be able to open this file if you double click it, but you will not be able to edit it and then save the changes.  That will help you understand the file system from a Graphical point of view.  Enjoy!

Shane

---

### Post by fragos on 2006-12-26
> **shane2peru said:**
> Hey, thanks!!!  That is nice to know.  I will have to check that out.  That is a lot easier for newbies!  Especially since Edgy switched to using the numbers.  I know you can do it without the numbers, but I would be curious if using this method wrote the fstab with the number system.  

Shane

Here's my fstab and yes the numbers are there.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda2 -- converted during upgrade to edgy
UUID=3c8fc8cc-d028-46cc-b121-059789ba1e4c  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda3 -- converted during upgrade to edgy
UUID=9175815c-7f6e-4f38-a3b5-72dd303e6530  /Other         ext3         defaults                    0  2  
# /dev/hda5 -- converted during upgrade to edgy
UUID=20247a1a-57c3-4127-88a8-f71c07766611  /Share         ext3         defaults                    0  2  
# /dev/hda1 -- converted during upgrade to edgy
UUID=97931eec-f0c9-46f4-a0cd-0f7a9272fb66  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/hda1                                  /media/hda1    swap         defaults                    0  0  
/dev/hda3                                  /media/hda3    ext3         defaults                    0  0  
/dev/hda2                                  /media/hda2    ext3         defaults                    0  0  
/dev/hda5                                  /media/hda5    ext3         defaults                    0  0

---

### Post by shane2peru on 2006-12-26
> **fragos said:**
> Here's my fstab and yes the numbers are there.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda2 -- converted during upgrade to edgy
UUID=3c8fc8cc-d028-46cc-b121-059789ba1e4c  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/hda3 -- converted during upgrade to edgy
UUID=9175815c-7f6e-4f38-a3b5-72dd303e6530  /Other         ext3         defaults                    0  2  
# /dev/hda5 -- converted during upgrade to edgy
UUID=20247a1a-57c3-4127-88a8-f71c07766611  /Share         ext3         defaults                    0  2  
# /dev/hda1 -- converted during upgrade to edgy
UUID=97931eec-f0c9-46f4-a0cd-0f7a9272fb66  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/hda1                                  /media/hda1    swap         defaults                    0  0  
/dev/hda3                                  /media/hda3    ext3         defaults                    0  0  
/dev/hda2                                  /media/hda2    ext3         defaults                    0  0  
/dev/hda5                                  /media/hda5    ext3         defaults                    0  0
Ok, thanks fragos.

Shane

---

### Post by fragos on 2006-12-26
And thank you for your service to God.

---

