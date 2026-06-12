---
title: "Add other (internal) hard drives permanently to dash search?"
date: 2014-12-20
forum: General Help
---

### Post by petermartin2 on 2014-12-20
I have two internal hard drives where I keep 95% of all my files and don't have an effective way to search them. So far I have been using XBMC that came with the Ubuntu After Install package to search my extensive movies folder but there's really no good way to search the rest of my files (I have 5TB+ of movies, music and a lot of photos and text docs). It would be incredibly convenient if I could search all my internal hard drives for files from dash. Can I do this?

---

### Post by carl4926 on 2014-12-20
So is the hdd in question visible in the dash, it should be
But not all hdd's or partitions to be exact, that show in the dash will be already mounted at boot. You have to click it to mount it.
Beyond that you'd need to have it mount at boot by editing that requirement in to /etc/fstab

---

### Post by petermartin2 on 2014-12-20
> **carl4926 said:**
> So is the hdd in question visible in the dash, it should be
But not all hdd's or partitions to be exact, that show in the dash will be already mounted at boot. You have to click it to mount it.
Beyond that you'd need to have it mount at boot by editing that requirement in to /etc/fstab

It's not locked to the dashmenu. It's visible in files on startup and once clicked it mounts. Is it enough to just write /etc/fstab? I'm new on ubuntu. I'm trying to follow this guide [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) but on the step how to find out if the harddrive is ext 3 or ext 4 etc gparted don't even show the other internal hard drives (even when they are mounted) so I can't get that information

---

### Post by carl4926 on 2014-12-20
The info there looks to me OK
But let's see

```
sudo cat /etc/fstab
```

```
sudo parted -l
```

---

### Post by petermartin2 on 2014-12-20
Thanks! The second command gave me the information about the hard drives but they still won't show in gparted..

---

### Post by carl4926 on 2014-12-20
I need to see the results

---

### Post by petermartin2 on 2014-12-21
> **carl4926 said:**
> I need to see the results

Of course, I am so sorry;

[HTML]peter@peter:~$ sudo cat /etc/fstab/
[sudo] password for peter: 
cat: /etc/fstab/: Not a directory
peter@peter:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=22bd91c2-e412-4635-a657-3e2e9167b09e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=02dd8005-5cf8-44df-ac8b-488f42308206 none            swap    sw              0       0[/HTML]

[HTML]peter@peter:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   349GB  349GB   primary   ntfs
 3      349GB   488GB  138GB   extended
 5      349GB   350GB  257MB   logical   ext2
 6      350GB   354GB  4095MB  logical   linux-swap(v1)
 8      354GB   378GB  24,0GB  logical   ext4
 7      378GB   488GB  110GB   logical
 4      488GB   500GB  12,6GB  primary   ntfs            diag


Model: ATA Hitachi HDS72404 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17,4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   4001GB  4001GB  ntfs         Basic data partition          msftdata


Model: ATA Hitachi HDS72404 (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17,4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   4001GB  4001GB  ntfs         Basic data partition          msftdata


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: TSSTcorp CDDVDW SH-224BB (scsi)                                    
Disk /dev/sr0: 2048B
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: [/HTML]

---

### Post by carl4926 on 2014-12-21
Strange thing is
All my partitions show in dash. (Just to be clear, you mean the launcher right?) Dash is actually something else.

I would like to know, if you create a new user and login there, if you still don't have the partitions in the launcher

Can you also post
```
sudo fdisk -l
```

---

### Post by carl4926 on 2014-12-21
> **carl4926 said:**
> Strange thing is
All my partitions show in dash. (Just to be clear, you mean the launcher right?) Dash is actually something else.

I would like to know, if you create a new user and login there, if you still don't have the partitions in the launcher

Can you also post
```
sudo fdisk -l
```


Would also be helpful to have
```
[COLOR=#111111][FONT=Consolas]sudo blkid[/FONT][/COLOR]
```

---

### Post by petermartin2 on 2014-12-25
I have unlocked the internal hard drives from the launcher. Are you suggesting that this is the reason why they don't show when I search in unity dash? I am sorry if I have not been clear in the explanation of my problem. I am looking for a way to 

a) search the entire content of all my internal harddrives for a file or folder

if this is not possible I want to 

b) have a way to search the internal hard drives one by one for a file or folder

Thanks..

---

### Post by petermartin2 on 2014-12-25
If the reason why I can't search them is that they are unlocked from the launcher could someone please tell me how I could get them on the launcher again?

---

### Post by mc4man on 2014-12-25
You can add them back to launcher thru dconf-editor ( com > canonical > unity > devices by removing from the Blacklist but that's likely not your issue.
The Files & Folders lens in Unity Dash isn't going to return search results on files in those volumes unless you've accessed the file your searching for previously.
Use your file manager search instead

---

### Post by petermartin2 on 2014-12-25
> **mc4man said:**
> You can add them back to launcher thru dconf-editor ( com > canonical > unity > devices by removing from the Blacklist but that's likely not your issue.
The Files & Folders lens in Unity Dash isn't going to return search results on files in those volumes unless you've accessed the file your searching for previously.
Use your file manager search instead

Ok thanks I found the search option in file manager it works fine!

---

### Post by mc4man on 2014-12-25
If you have nautilus then there are 2 search methods - 
The search icon (looking glass), this does recursive searchs from present dir >  in
There is also a type-ahead find > just start typing beginning of file name, ect. This just works in current dir.

---

### Post by petermartin2 on 2014-12-25
> **mc4man said:**
> If you have nautilus then there are 2 search methods - 
The search icon (looking glass), this does recursive searchs from present dir >  in
There is also a type-ahead find > just start typing beginning of file name, ect. This just works in current dir.

Yes this was my problem I thought the current dir search was the only search

---

