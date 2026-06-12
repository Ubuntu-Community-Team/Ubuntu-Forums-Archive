---
title: "external hd's won't mount on Ubuntu Studio."
date: 2023-08-27
forum: General Help
---

### Post by midwestman76 on 2023-08-27
I have 3 external hd's. All would mount with no problem. Now 2 get a unknown mounting error & 1 of the 3 mounts every time. What changed. Thanks for any ideas.

---

### Post by yancek on 2023-08-27
I expect you would be the best person to know 'what changed'.  Did you do any recent updates or make any changes to the system?  Have you had these drives mount previously from entries in the /etc/fstab file?  Or did they show as accessible under /media/username?  Or did you manually mount them?  Do you have mount points set for all 3 and if so, are they in the /etc/fstab file?  Generally not a good idea to have external drive mounts in fstab unless you plan to keep them permanently attached.  Are they connect directly to a USB port and do you use the same port for each everytime and connect them in the same order?

---

### Post by ajgreeny on 2023-08-27
Have you recently attached them to a Windows computer and then unplugged them before going through the "Remove hardware safely" or however Windows now describes it.

I haven't used Windows properly for 18 years so I don't know how it words that removal method now but I'm sure you will know what I mean.

---

### Post by midwestman76 on 2023-09-04
Sorry for the delay. I can't recall any changes, I just keep the system updated from time to time. I have the 3 HD's conneted to a 4 into 1 usb. They all mounted automatically just fine for months, then one day 2 would get unknown errors and not mount and one still mounts every time.The rest of your questions go over my head. At 69 yrs I'm not as on the ball as I used to be. Thanks for the input though.

---

### Post by midwestman76 on 2023-09-04
No I haven't attached them to a windows computer.

---

### Post by ajgreeny on 2023-09-05
How are those disks formatted; what filesystem, and do you try to mount them simply by clicking on them in the file manager or are they listed in the /etc/fstab file?

As mentioned above, external disks do not mount by default at boot unless they are set to do so in the /etc/fstab file.

---

### Post by midwestman76 on 2023-09-05
Ok, the one that mounts is ntfs3 and mounted on   /media/grocker/Expansion Drive (E) mounted from   
/dev/sda1  i don't know what the 2 that stopped mounting are since I can't access them.

---

### Post by yancek on 2023-09-05
Check the fstab file as suggested above.  That will show whether any/all are set to mount on boot.  You can see this information with the command:  cat /etc/fstab
 
>   i don't know what the 2 that stopped mounting are since I can't access them. 		

In your original post, you indicate that all would mount with no problem previously.l  How?  Did you manually mount them?  External drives are generally available under the /media/username directory.  Do you see them there?  What specific error do you get and how do you get it?  Manually trying to mount?  Some other way?  Have you checked the connections on the 2 drives that won't mount?

---

### Post by midwestman76 on 2023-09-05
[FONT=monospace][COLOR=#54ff54]**grocker@grocker-hpelitebook755g5**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/fstab [/COLOR]
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a device; this may 
# be used with UUID= as a more robust way to name devices that works even if 
# disks are added and removed. See fstab(5). 
# 
# <file system>             <mount point>  <type>  <options>  <dump>  <pass> 
UUID=2335-E3DC                            /boot/efi      vfat    umask=0077 0 2 
UUID=9957462d-b344-4364-8fe4-8b5909cf7a23 /              ext4    defaults,discard 0 1 
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0 
[COLOR=#54ff54]**grocker@grocker-hpelitebook755g5**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  [/COLOR]



[/FONT]

---

### Post by midwestman76 on 2023-09-05
All the drives show up on dolphin. The 2 that won't mount say   An error occurred while accessing 'Seagate Expansion Drive', the system responded: The requested operation has failed: Error mounting /dev/sdc2 at /media/grocker/Seagate Expansion Drive: Unknown error when mounting /dev/sdc2

---

### Post by yancek on 2023-09-05
>   			 			All the drives show up on dolphin

Are you able to access them in Dolphin?  Do you need to use sudo to access them?  If you are trying to mount in a terminal that won't work with the directory name as you cannot have spaces in a directory/file name.  From a terminal, if the name for the mount point is Seagate Expansion Drive, you need to use the command below with quotes around the name.

```
 sudo mount /dev/sdc2 "/media/grocker/Seagate Expansion Drive"
``` 

Please clarify how you are trying to access the drive and faileing.

---

### Post by midwestman76 on 2023-09-06
When I can afford to pick up a Windows laptop I'll try the hd's on it and see what happens. Thanks for the help.

---

### Post by midwestman76 on 2023-09-06
[FONT=monospace][COLOR=#000000]mount: /media/grocker/Seagate Expansion Drive: mount point does not exist.[/COLOR]
[/FONT]

---

### Post by midwestman76 on 2023-09-06
I push the button on  the expansion port the seagate is attached to. Dolphin opens and gives the unknown error that it can't mount the drive

---

### Post by yancek on 2023-09-07
> [FONT=monospace][COLOR=#000000]mount: /media/grocker/Seagate Expansion Drive: mount point does not exist.[/COLOR][/FONT] 

Did you see my suggestion in post 11?  You need quotes around it as the name has spaces in it so the mount command will see the mount point as Seagate whcih explains why you get the error.

---

### Post by TheFu on 2023-09-07
It is best to follow these rules for Linux storage.

Don't use NTFS unless required - meaning the storage will be physically connected to an MS-Windows computer - that is DIRECTLY wired using SATA/eSATA/USB. Network connections don't count.
Don't use FAT32, exFAT, or vFAT unless required.

Some devices may need exFAT or FAT32 to work. Cameras, smartphones typically do.

Use native Linux file systems for Linux needs.  These are ext4 for HDD/SSDs or fs2fs for flash storage.

Ok, now ... for things that can help.

Always set the LABEL on a new partition so that is unique and doesn't contain spaces.  Spaces are possible in LABELs, but they cause problems if we aren't very careful.
Avoid using USB connected storage long term.  USB connections drop sometimes.  I see it happen about once a month myself.  I'm not the only one.  When storage becomes disconnected unexpectedly, it needs an **fsck** to correct any issues.  For native Linux file systems, that's provided with the file system tools, but for non-native file systems like NTFS, FAT32, exFAT, you'll need MS-Windows to check the file system.

By default, native linux file systems should automatically run fsck every 30 days, but there may be differences in the defaults on your system.  It doesn't hurt to check.  **tune2fs -l** is the command to check the settings.  You'll need to provide the full path to the device file for the partition/file system to use the tune2fs command.

---

### Post by midwestman76 on 2023-09-08
Thank you for trying to help. I just reworded my question on a search engine & opened the first newest post and I tried the suggestion  sudo ntfsfix /dev/ 'name of drive" and it worked. repaired both drives and they mounted like usual.

---

### Post by midwestman76 on 2023-09-08
Ok, Thanks. Good information. I'm still trying to learn linux.

---

### Post by TheFu on 2023-09-08
> **midwestman76 said:**
> Thank you for trying to help. I just reworded my question on a search engine & opened the first newest post and I tried the suggestion  sudo ntfsfix /dev/ 'name of drive" and it worked. repaired both drives and they mounted like usual.

a) beware that all NTFS tools on Linux are reverse engineered and lack full capabilities.  In short, don't trust them. They are a hack. All of them.

b) If you've solved this issue, please help safe other people some time and mark the thread as SOLVED using the "thread tools" button.

c) Move off NTFS for all storage that is only going to be connected to Linux.

---

