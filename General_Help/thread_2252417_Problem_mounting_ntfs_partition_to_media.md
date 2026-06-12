---
title: "Problem mounting ntfs partition to /media"
date: 2014-11-11
forum: General Help
---

### Post by t-iimm-k on 2014-11-11
I'm fairly new to linux and I've been trying to synchronise my music on my dual boot system (windows 8 and ubuntu 14.04).

I have tried manually editing fstab and using the disks program, but no matter what tutorial I follow I get an error on startup saying that an error occured while mounting to /media/storage (I made the storage folder and I want to mount to media so that the drive shows up in the places menu).

here is the blkid (the drive I'm attempting to mount is labeled gen-storage):
tim@tim-pc1:~$ sudo blkid
/dev/sda1: LABEL="WINRE_DRV" UUID="8A043EA6043E9563" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM_DRV" UUID="EE41-0723" TYPE="vfat" 
/dev/sda3: LABEL="LRS_ESP" UUID="8241-4B8C" TYPE="vfat" 
/dev/sda5: LABEL="Windows8_OS" UUID="983444A634448968" TYPE="ntfs" 
/dev/sda6: LABEL="gen-storage" UUID="EE24706024702DA9" TYPE="ntfs" 
/dev/sda7: UUID="84e87c04-5a35-453c-82fe-435ee00ff863" TYPE="ext4" 
/dev/sda8: UUID="22c03c2e-cb96-44fd-b26e-254bc8d7887e" TYPE="swap" 
/dev/sda9: UUID="80f099b5-7cb5-4f7a-8ed7-714c6dde26bc" TYPE="ext4" 
/dev/sda10: UUID="941E2E671E2E429A" TYPE="ntfs" 
/dev/sda11: LABEL="LENOVO" UUID="CA984AD5984ABFA5" TYPE="ntfs" 
/dev/sda12: LABEL="PBR_DRV" UUID="9AFA46DDFA46B573" TYPE="ntfs"


here is an example of one way I have tried to change the fstab file (from a tutorial):

[FONT=arial]# storage mount
UUID=EE24706024702DA9 /media/storage/    ntfs-3g        auto,user,rw 0 0


What am I doing wrong?[/FONT]

---

### Post by ajgreeny on 2014-11-11
What error message does the command **sudo mount -a** in terminal show you?

---

### Post by t-iimm-k on 2014-11-11
tim@tim-pc1:~$ sudo mount -a /dev/sda6 /media/storage
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by coffeecat on 2014-11-11
I notice you appear to have Windows 8 installed. Have you disabled fastboot in Windows 8? Fastboot means that Windows is hibernated, not shut down, and this can lead to the sort of problem you are seeing  in that mount output with a shared NTFS partition. 

By the way, ajgreeny suggested the command "sudo mount -a", without the bit you added. Although your command gave the information needed, mount -a is a very useful command as it causes the system to parse /etc/fstab.

---

### Post by t-iimm-k on 2014-11-11
I have already disabled fast boot.
(also that's good to know, I was confused at first because I had reset my fstab file so the command gave me no feedback)

---

### Post by coffeecat on 2014-11-11
OK, so the first line of the error message is probably the issue here. Try running a chkdsk from Windows. If Ubuntu detects an unclean fileystem it will usually refuse to mount it.

---

### Post by t-iimm-k on 2014-11-11
thanks I'll try this. Out of curiosity why might a newly formatted partition be unclean (and what exactly does that mean)? All I did was shrink my windows partition, format the extra space as ntfs and move over some music files onto it.

---

### Post by coffeecat on 2014-11-11
You're right. A new filesystem should not be unclean. However, you do say you moved some files over into it. Perhaps some sort of error occurred then. It will be interesting to see if chkdsk reports anything significant.

---

### Post by t-iimm-k on 2014-11-11
I went to the drive in the explorer in windows, and through properties checked the disk and it said no errors were found.

---

### Post by yancek on 2014-11-11
I think what was suggested above it to boot into windows and run the command chkdsk as explained at the link below.   

[http://www.tekrevue.com/tip/how-to-scan-fix-hard-drives-with-chkdsk-in-windows-8/](http://www.tekrevue.com/tip/how-to-scan-fix-hard-drives-with-chkdsk-in-windows-8/)

---

### Post by t-iimm-k on 2014-11-11
So it turns out I didn't know enough about this to realize I had to run some commands to change the ownership and permission of the folder I created to be the mount point. I don't know why that wouldn't have been mentioned in a tutorial for newbs but anyway it works now, thanks for the suggestions.

---

### Post by coffeecat on 2014-11-12
I’m glad your problem seems to be solved. However, your last post raises more questions. Some thoughts for you.

Although Windows said it found no errors on that partition, Windows must have done something. Ubuntu was telling you that either the file system was unclean, or that there was metadata in the cache. I *think* the latter means that Ubuntu found a hibernation file which wouldn’t bother Windows but would prevent Ubuntu from mounting the partition. If Ubuntu had indeed detected a hibernation file then although you said you had disabled fast boot, I wonder if Windows hadn’t actually yet cleaned the filesystem properly when you saw that error message but had done so by the time you mounted the partition sucessfully. Because... 

[quote=t-iim-k]I had to run some commands to change the ownership and permission of the folder I created to be the mount point.[/quote]

This would have done absolutely nothing to fix your problem, I can assure you. Changing the ownership and permissions of a folder to be used a mountpoint but without anything mounted is a waste of time, because the ownership and permissions are overridden by mount options or the filesystem itself when something is mounted to it. And you cannot change the ownership and permissions of a mounted NTFS filesystem with chown and chmod commands because NTFS doesn’t support Linux permissions. The only way of changing ownership and permissions of a mounted NTFS filesystem in Linux is by means of mount options.

Which leads to (from your first post)...

[quote=t-iim-k]UUID=EE24706024702DA9 /media/storage/ ntfs-3g auto,user,rw 0 0[/quote]

That’s not a set of mount options I would use myself. And...

[quote=t-iim-k]I don't know why that wouldn't have been mentioned in a tutorial for newbs but anyway it works now[/quote]

Do you have a link to the tutorial? Here’s another one:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

From that wiki page, I would recommend you use the /etc/fstab line under the line “For a general-purpose read-write mount” which adapted with your UUID and mountpoint would give:

```
 UUID=EE24706024702DA9 /media/storage  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```

Change the locale to yours as described in that page. Apart from the locale change, those are the options I use and the use of windows_names is very important with a partition shared with Windows.

[http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)

> 
windows_names

This option prevents files, directories and extended attributes to be created with a name not allowed by windows, either because it contains some not allowed character (which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) or because the last character is a space or a dot. Existing such files can still be read (and renamed).


Ubuntu will happily save a file to NTFS and read it with a filename containing : < > and so on if you don’t use that option. Windows gives you an error when confronted with the same file. You’ll save yourself a lot of time and puzzlement if you use the windows_names mount option.

---

### Post by Mark Phelps on 2014-11-12
> I have already disabled fast boot.

It's not "fast boot"; instead, it's "fast startup" -- that's what needs to be disabled in Win8.

---

