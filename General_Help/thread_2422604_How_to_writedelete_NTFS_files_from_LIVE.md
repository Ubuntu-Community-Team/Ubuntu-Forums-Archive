---
title: "How to write/delete NTFS files from LIVE?"
date: 2019-07-10
forum: General Help
---

### Post by gordan-vrbanec-vepar on 2019-07-10
I am extremely new to ubuntu. I have used it several time throughout the years, but never mastered it so please someone help a newbie out.
If possible some step by step guide so i can follow it. I cant even install my keyboard layout so i cant find most of the punctuation, sorry about that.

Recently my windows crashed and i cant get it back i need to install a new one. The problem is, i need to move and delete some files from the C: folder where i plan on installing windows, but i cant delete or move them to another ntfs partition. I can mount the drives but i cant write a new folder or anything on NTFS nor can i delete anything.

I tried searching the net but i dont understand any of it and most of them use the installed ubuntu version. I am on live USB. Some say to chown the drive, but how do i do that from the live USB? There is no user or password. Others mention ntfsfix but that did nothing either. 

What do i do?
I have some important files to move, otherwise i would just format the drive entirely and get it over with...

I am using ubuntu 18.04.

Thank you for your help!

---

### Post by TheFu on 2019-07-10
Windows problems should be fixed using Windows.

You cannot chown NTFS file systems without doing some advanced mapping. Mount options control the normal Unix permissions for NTFS and other non-Linux file system types.

If you want to wipe Windows and using Ubuntu, we can help, but to fix Windows issues, using Windows it the best method.

---

### Post by gordan-vrbanec-vepar on 2019-07-10
But my only option using windows is formatting the disk and losing my data. I tried all the recovery options and none of them worked...
Also, how is moving files from one disk to another a windows issue? I just need to move some critical files, nothing else. Shouldnt that be simple?

---

### Post by TheFu on 2019-07-10
NTFS is a proprietary Windows file system.  It isn't a native-to-Linux file system.   Blame Microsoft.  [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup) has more details.  It is a well-know issue with Windows. That's my guess today.

I know of no work-around for the fast-boot problem in Windows except to use Windows to fix it. Sorry.

Reading might work, provided NTFS file system(s) are in a known state or closed. Writing/moving is more complex because the NTFS file system drivers don't map Windows permissions to Linux permissions.  Don't move - try copy.  Don't worry about deleting. When you reinstall Windows, just overwrite, format, everything.

In Linux, the mapping of NTFS permissions are addressed at mount time. This means the userid, group and permissions are controled at mount time.  If you use a GUI to initially "mount" the storage for either the source or the target partition, I don't know of any method to control those important settings.  In a shell/CLI interface, we can control them with the mount command.

I wish there were a few commands I could tell you to type, but before that is possible, information is needed.  Connect the source and target disk devices and run
**sudo parted -l** to gather some initial information. We might need more, but this might be sufficient.
Also, if you could point out which is the source partition and which is the target partition, 

Also, when posting the parted output, please use code tags- Adv Reply (#). This will have things lined up which is much easier to read. The advanced editor has a button, #.

---

### Post by gordan-vrbanec-vepar on 2019-07-10
I see. That makes sense. I was not aware of fast boot and how it affects things in linux!
The  last time i needed this was in windows 7, and then after a few commands  i could write on NTFS. Did not know things got more complicated.
Thank you for explaining!

Here is the output from sudo parted -l:

```
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  577MB  576MB  primary  ntfs         boot
 2      577MB   250GB  249GB  primary  ntfs


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size   Type      File system  Flags
 1      1049kB  525MB   524MB  primary   ntfs         boot
 2      525MB   225GB   225GB  primary   ntfs
 3      225GB   226GB   490MB  primary   ntfs         diag
 4      226GB   1000GB  775GB  extended
 5      230GB   1000GB  770GB  logical   ntfs


Model: Kingston DT101 II (scsi)
Disk /dev/sdc: 8006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8006MB  8005MB  primary  fat32        boot, lba


Model: JetFlash Transcend 16GB (scsi)
Disk /dev/sdd: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  16.1GB  16.1GB  primary  fat32        boot, lba

```

Source partition is /dev/sda disk, the SSD where i keep windows.
Target partition is /dev/sdb disk which is the backup HDD for files etc.

---

### Post by TheFu on 2019-07-10
Read everything carefully, please.

sda and sdb aren't sufficient details.  We need the exact partition number.  Windows isn't clear that there is a difference between a "disk" and a "partition", which is unfortunate.  Linux cares.  Get the wrong one and it will be bad.

Looks like the source is sda2, but I can't guess which  of sdb2 or sdb5 are the target.  All NTFS, eeeew. I feel dirty.  Let me see if I can find a mount statement that you can modify for your needs.

So, first we need some empty directories to serve as 
```
sudo mkdir /mnt/source /mnt/target
```

Now let's mount the source.
```
sudo mount -t ntfs -o uid=1000,gid=1000,fmask=0002,dmask=0002,big_writes /dev/sda2  /mnt/source
```
This assumes that the userid you are running under is 1000 with a gid of 1000. You can check that using the 'id' command in a terminal.
```
sudo mount -t ntfs -o uid=1000,gid=1000,fmask=0002,dmask=0002,big_writes /dev/sdbX  /mnt/target
```
You'll have to change the **X** to be the correct number.
Assuming there aren't any errors, continue.  The "big_writes" option should help performance on NTFS about 30%.

Now you can use the file manager to copy over files. In theory, the storage should be owned by your userid and have permissions so you can write.

Either reboot or use umount to disconnect the mounts. DO NOT JUST PULL THEM OUT!  Inside a file manager, you cannot "eject" the mounts either.  Only a shutdown, reboot or umount will work.

---

### Post by gordan-vrbanec-vepar on 2019-07-10
Yeah, ntfs to ntfs... :( If i had another drive that is not ntfs i could just copy from ntfs, that works without any issues i think, but alas, i do not.

You were right, the source is sda2 and teh target is sdb5. Sorry i should have included that information.

The id command returns this:


```
uid=999(ubuntu) gid=999(ubuntu) groups=999(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)
```

I tried running this command:

```
[COLOR=#000000][FONT=&amp]sudo mount -t ntfs -o uid=1000,gid=1000,fmask=0002,dmask=0002,big_writes /dev/sda2  /mnt/source[/FONT][/COLOR]
```
 
and i get this output:
```
ig_writes /dev/sda2  /mnt/sourceWindows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

```

Now i understand what you meant by fast boot and windows itself being the problem. This was no doubt caused by fast boot or something similar happening. And windows did not shut down because it crashed...

Nevertheless i tried changing uid and gid to what the "id" command told me and i get this:

```
Mount is denied because the NTFS volume is already exclusively opened.The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

```

Probably because it refused to mount it in the first place, so now it's locked or something. I can't even find it in the built in file manager anymore. 

I suppose a restart of the live session would be required to reset this, but i'm downloading windows right now, with an abysmally slow connection and it'll take a while.
I'll leave it overnight and try again tomorrow (replacing 1000 with 999 if that's needed). If it doesn't work (which is likely because apparently windows didn't shut down properly), then i'll just take the SSD to a friend and move my files that way...
I really need to get an external disk or something. Oh well...

In any case, thank you so much for trying to help me!

EDIT:

The second code went without errors, but i still can't write anything to now mounted /dev/sdb5.
Both source and target are in the /mnt directory, but it's the same as if they were mounted normally. Can't do anything, just browse.

---

### Post by Impavidus on 2019-07-11
If you can't write to your internal backup hard drive, try a usb drive. It's best to keep backups on an external drive anyway.

---

### Post by TheFu on 2019-07-11
Yes, the 1000 need to be 999, based on the output from 'id'.  The 1000 won't work for that live flash "try ubuntu" boot, it seems.
Do you understand the relationship between
[LIST]
[*]username
[*]userid
[*]uid
[/LIST]

?
> 
The second code went without errors, but i still can't write anything to now mounted /dev/sdb5.
Because the wrong uid/gid were used for the account being used.  I guessed "1000" for both, which works on a normal install for the 1st account created at install time.  The *Try Ubuntu* stuff apparently uses 999 instead.  If you change those correctly and remount, then you should be able to write to the other disk ... assuming it wasn't part of the *fast boot* stuff.  I've never touched Win10.

---

### Post by oldfred on 2019-07-11
You may just need to run chkdsk or turn off fast start up.
And you can only do either from Windows repair console with Windows installer or repair disk.

       Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by gordan-vrbanec-vepar on 2019-07-11
> **Impavidus said:**
> If you can't write to your internal backup hard drive, try a usb drive. It's best to keep backups on an external drive anyway.

I know but i don't have one at the moment. I have a small USB where i backed up the most critical of files, and if i can't fix this today, i'll just have to live withot the rest.
I have to get this finished today, cause i need a working computer lol.


> **TheFu said:**
> Yes, the 1000 need to be 999, based on the output from 'id'. The 1000 won't work for that live flash "try ubuntu" boot, it seems.
Do you understand the relationship between
[LIST]
[*]username
[*]userid
[*]uid
[/LIST]

?

Because the wrong uid/gid were used for the account being used. I guessed "1000" for both, which works on a normal install for the 1st account created at install time. The *Try Ubuntu* stuff apparently uses 999 instead. If you change those correctly and remount, then you should be able to write to the other disk ... assuming it wasn't part of the *fast boot* stuff. I've never touched Win10.

I will try that now, set both to 999, see what happens. 
And no, i don't understand the relationship between username, userid and uid. Sorry. 

> **oldfred said:**
> You may just need to run chkdsk or turn off fast start up.
And you can only do either from Windows repair console with Windows installer or repair disk.

       Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

That's exactly the problem. I get booted into windows repair thing they have, but i can't leave. Every option, including chkdsk, did nothing.
I tried booting up previous image, recovering windows, installing windows again and keepeng files (from recovery, like a refresh), every recovery option available and none of them worked. 
The installation is busted, there's nothing i can do about it now except do a clean install.

Thanks for the links, i know most of them and have tried such methods. But alas, it really seems it's crashed beyond repair. 
I'm downloading a fresh copy right now. If what TheFu worte won't work, i'll just have to lose some data. I backed up the most critical files to an USB, so it shouldn't be too much of a loss.

---

### Post by gordan-vrbanec-vepar on 2019-07-11
> **TheFu said:**
> Yes, the 1000 need to be 999, based on the output from 'id'.  The 1000 won't work for that live flash "try ubuntu" boot, it seems.
Do you understand the relationship between
[LIST]
[*]username 
[*]userid 
[*]uid 
[/LIST]

?

Because the wrong uid/gid were used for the account being used.  I guessed "1000" for both, which works on a normal install for the 1st account created at install time.  The *Try Ubuntu* stuff apparently uses 999 instead.  If you change those correctly and remount, then you should be able to write to the other disk ... assuming it wasn't part of the *fast boot* stuff.  I've never touched Win10.

Ok, i restarted, and changed 1000 to 999 in both instances, and it worked! I just created a new folder on /dev/sdb5!!!
Thank you so much! You just saved the rest of my data! :D
I will mark this thread solved now.
 
Thank you everyone for replying and especially TheFu for figuring out how to write to ntfs!

---

### Post by TheFu on 2019-07-11
```
uid=999(ubuntu) gid=999(ubuntu) groups=999(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)
sudo mount -t ntfs -o uid=1000,gid=1000,fmask=0002,dmask=0002,big_writes /dev/sda2  /mnt/source
```

See how the uid and gid numbers in the 'id' output map into the mount command options for uid/gid?  They should be the same most of the time - really always - but I've learned to avoid "always" and "never" over the decades.  There are **always** exceptions.

The fmask and dmask weren't strictly needed. The defaults are basically 777 permissions which I'd never allow.  The masks I used above are for 775 permissions.  Don't be lazy and use 777 anywhere.  I can think of 1 exception and the OS sets it up for us already to be a good trade-off.  /tmp/.  A web app that needs uploads might choose to have 1 directory setup to allow anyone to upload, but it shouldn't allow read access too and the webapp should pull those files immediately out of that directory for sanity processing.  So --- even the other exceptions shouldn't be 777 permissions.   666 is just as bad, BTW.  These are habits to cultivate even when they aren't that important - like a non-networked, single-user, Unix.

---

### Post by missmoondog on 2019-07-11
wow! all i can say is for some one who is new to linux, you sure got this figured out relatively quick. i don't know if i could've gotten it done even with the great advice from thefu! i'd still be asking tons of questions, and getting frustrated at myself!!

great job to OP and an extra thanks for the folks helping him out on this issue :)

---

