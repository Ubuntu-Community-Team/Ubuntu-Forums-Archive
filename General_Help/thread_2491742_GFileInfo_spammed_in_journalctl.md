---
title: "GFileInfo spammed in journalctl"
date: 2023-10-19
forum: General Help
---

### Post by darskx on 2023-10-19
hi, 

I'm using Xubuntu with 6.5.0.9 kernel, and I have noticed my journalctl  is getting spammed with the following messages, 100 of entries at a  time;

GFileInfo created without standard::is-hidden
 Thunar[517129]: file ../../../gio/gfileinfo.c: line 1633 (g_file_info_get_is_hidden): should not be reached
 Thunar[517129]: GFileInfo created without standard::is-backup
Thunar[517129]: file ../../../gio/gfileinfo.c: line 1655 (g_file_info_get_is_backup): should not be reached
 Thunar[517129]: GFileInfo created without standard::is-symlink
 Thunar[517129]: file ../../../gio/gfileinfo.c: line 1677 (g_file_info_get_is_symlink): should not be reached

This usually happens when I'm copying files between drives. sometimes also things can take a little longer to open or load.

is this anything I need to be concerned about?

darsk

---

### Post by ActionParsnip on 2023-10-19
Possibly related
[https://gitlab.gnome.org/GNOME/gimp/-/issues/9994](https://gitlab.gnome.org/GNOME/gimp/-/issues/9994)

---

### Post by MAFoElffen on 2023-10-19
The original Launchpad Bug that triggered that: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2025290](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2025290)

If related, please join that Bug as "Also Affected."

---

### Post by TheFu on 2023-10-19
Avoid using GIO and GVFS.  That means don't use fake mounts, only real mounts which happen through one of 3 methods:

/etc/fstab
sudo mount
or using autofs.

If you are point-n-clicking to cause a "magic mount", that's usually the hint that gio/gvfs are being used.  Plus, those tend to be slower connections. Drastically slower, though the Gnome project claimed they were trying to fix the performance issues a few years ago, I have doubts.  OTOH, I don't use either gio/gvfs.

---

### Post by darskx on 2023-10-19
This is only happening in Xubuntu 23.10, I have a PC still running 23.04 and this isn't an issue.

I usually do mount drives in Thunar, not the terminal. will definitely try that instead.

Ive been having to mount an external drive as read only in terminal, as it will just hang my system when copying files otherwise.

Thank you for all the replies

---

### Post by TheFu on 2023-10-19
Which file system?  **df -Th** will show them.

---

### Post by darskx on 2023-10-19
> **TheFu said:**
> Which file system?  **df -Th** will show them.

Heres the output from running df-Th

Filesystem     Type      Size  Used Avail Use% Mounted on
tmpfs          tmpfs     3.2G  2.6M  3.2G   1% /run
/dev/sdf2      ext4      1.8T  1.6T  134G  93% /
tmpfs          tmpfs      16G  627M   15G   4% /dev/shm
tmpfs          tmpfs     5.0M   20K  5.0M   1% /run/lock
efivarfs       efivarfs  256K  133K  119K  53% /sys/firmware/efi/efivars
/dev/sdf1      vfat      511M  6.1M  505M   2% /boot/efi
tmpfs          tmpfs     3.2G  7.1M  3.2G   1% /run/user/1000
/dev/sde1      ntfs3     5.5T  5.5T   36G 100% /media/darsk/WD Black 
/dev/sdd1      ntfs3     5.5T  5.5T   46G 100% /media/darsk/WD Black 
/dev/sdc2      ntfs3     3.7T  3.6T   60G  99% /media/darsk/WD Black

---

### Post by TheFu on 2023-10-19
Dude, you can't mount or ask the different file systems to be mounted to the same location.
Much better to show the actual output than your interpretation.  Facts.

---

### Post by darskx on 2023-10-19
> **TheFu said:**
> Dude, you can't mount or ask the different file systems to be mounted to the same location.
Much better to show the actual output than your interpretation.  Facts.

Ive Edited my post to show the full output from the command.

---

### Post by TheFu on 2023-10-19
> **darskx said:**
> Heres the output from running df-Th

```

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdf2      ext4      1.8T  1.6T  134G  93% /
/dev/sdf1      vfat      511M  6.1M  505M   2% /boot/efi
/dev/sde1      ntfs3     5.5T  5.5T   36G 100% [COLOR="#FF0000"]/media/darsk/WD Black [/COLOR]
/dev/sdd1      ntfs3     5.5T  5.5T   46G 100% [COLOR="#FF0000"]/media/darsk/WD Black [/COLOR]
/dev/sdc2      ntfs3     3.7T  3.6T   60G  99% [COLOR="#FF0000"]/media/darsk/WD Black[/COLOR]
```

I added code tags and removed the crap that isn't real storage, hoping that makes it readable. I may not.  Regardless, you can't mount 3 different devices to the same directory as shown. Is something else happening here? Looks like some sort of merged file system or RAID-weirdness.  

Let's look at it from a slightly different perspective:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
Please use code tags in the output for that lsblk command, as without them it will be unreadable.

---

### Post by MAFoElffen on 2023-10-19
> **TheFu said:**
> I added code tags, hoping that makes it readable. I may not.  Regardless, you can't mount 3 different devices to the same directory as shown. Is something else happening here? Looks like some sort of merged file system or RAID-weirdness.  

Let's look at it from a slightly different perspective:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
Please use code tags in the output for that lsblk command, as without them it will be unreadable.
A quick and easy tip on posting with CODE Tags... On an existing post, select "Adv Reply"... Or at the bottom of the page, select "Go Advanced"... That will start the Advanced Editor, with an extended tool bar...

In that tool bar, you will see an "#" Icon. If you select that, it will insert Code Tags that will look like these (lets see if I can do some hacking magic to show you something that is usually invisible when displayed...)
```

**[COLOR=#ff0000][noparse][CODE]    
```[/noparse][/COLOR]**
[/code]
Or you could just manually type the tags as they are shown above... Then-- Paste your output between those two tags... If you preview it, or submit it, those Code Tags wrap the output with a Code Box in the post... It is a Forum policy to post all commands and output within Code tags. Besides being easier for us to read, sometimes not doing so does bad things to the software of the Forum... TheFu is trying to get you to start doing that before one of the Moderators notices... and gives you a stern warning about that.

[HR][/HR]
I would also like to see the output of this posted within CODE Tags
```

mount | grep 'media'

```
So I can see the mount options it is trying to apply to those...

---

### Post by darskx on 2023-10-19
```
 NAME   TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL               MOUNTPOINT
sda    disk        931.5G                                    
&#9500;&#9472;sda1 part vfat     100M                                    
&#9500;&#9472;sda2 part           16M                                    
&#9500;&#9472;sda3 part ntfs   930.9G                                    
&#9492;&#9472;sda4 part ntfs     537M                                    
sdb    disk        931.5G                                    
&#9500;&#9472;sdb1 part           16M                                    
&#9492;&#9472;sdb2 part ntfs   931.5G                Evo 860 1TB [Games] 
sdc    disk          3.6T                                    
&#9500;&#9472;sdc1 part           16M                                    
&#9492;&#9472;sdc2 part ntfs     3.6T   59.3G    98% WD Black 4TB [Data] /media/darsk/WD Bla
sdd    disk          5.5T                                    
&#9492;&#9472;sdd1 part ntfs     5.5T   45.2G    99% WD Black 6TB [Data] /media/darsk/WD Bla
sde    disk          5.5T                                    
&#9492;&#9472;sde1 part ntfs     5.5T   35.1G    99% WD Black 6TB [Data] /media/darsk/WD Bla
sdf    disk          1.8T                                    
&#9500;&#9472;sdf1 part vfat     512M  504.9M     1%                     /boot/efi
&#9492;&#9472;sdf2 part ext4     1.8T  126.8G    88%                     /
sdg    disk        115.3G                                    
&#9492;&#9472;sdg1 part exfat  115.3G                Kingston            
sr0    rom          1024M       
``` 


```
mount | grep 'media'

/dev/sde1 on /media/darsk/WD Black 6TB [Data] type ntfs3 (rw,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,uhelper=udisks2)
/dev/sdd1 on /media/darsk/WD Black 6TB [Data]1 type ntfs3 (rw,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,uhelper=udisks2)
/dev/sdc2 on /media/darsk/WD Black 4TB [Data] type ntfs3 (rw,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,uhelper=udisks2)

``` 


heres the output from both those commands, does this look normal?

Thanks for the advice, will start doing that.

darsk

---

### Post by TheFu on 2023-10-20
That does show the label names and that they aren't mounted to the same locations.

If it were me, I'd change the label for each of those drives to something unique and meaningful. Also, I'd manually mount them using the fstab - i.e. NOT using a GUI or the aid of udisks2.  The label names I'd give wouldn't have any spaces and would be meaningful to me.  Spaces and other odd characters, while they can be supported, often cause issues that can trivially be avoided.

And perhaps you'd consider using a native Linux file system. That's a bunch of data to be stuck in NTFS.  Always remember that NTFS is not a native file system to Linux and that support is reverse engineered without MSFT's help.

I have lots of storage connected to some of my systems. I never allow mounts under /media/ - been burned a few times with that.  And I have enough disks that I just mount them as 
```
/d/D1
/d/D2
/d/D3
/d/D6
/d/D7
/d/b-D1
/d/b-D2
/d/b-D3
/d/b-D6
/d/b-D7
```
Can you guess which are for backups for the media on the other half?  Can you guess which file systems used to exist, but had failures and were removed?  These aren't trick questions.  I'm happy to show my fstab for these, but since I use LVM2 for storage management, it might confuse things. Also, I avoid using NTFS whenever possible, so my mounts don't use it.

I'd like to be clear. NTFS is the best choice for file systems that are directly connected to MS-Windows and Linux computers, provided only data is stored there, not programs.

---

### Post by darskx on 2023-10-20
Thanks for you help TheFu

I have those drives as ntfs as I have Linux and Windows 10 on two separate ssds. 
Im not running any programs from them, just use them for media files, and backups of games etc.

I planning on building a NAS in the next few months, as I have way too much data I would hate to lose.

I was worried I didn't mount them correctly.

> I  have lots of storage connected to some of my systems. I never allow  mounts under /media/ - been burned a few times with that

Can I ask what you mean when you say you've been burned, what are the issues when drives are mounted under media?

>  Can you guess which are for backups for the media on the other half?

yeah, you made it pretty straight forward. O:) It does make sense, will look into renaming them.
I just left them with the names I assigned to them in windows, but these days I'm using windows less and less.
Still alot to learn, but im enjoying using linux, even for gaming.

>   I'm happy to show my fstab for these, but since I use LVM2 for storage  management, it might confuse things. Also, I avoid using NTFS whenever  possible, so my mounts don't use it.

Actually that would be very helpful if you don't mind doing that.

---

### Post by TheFu on 2023-10-20
> **darskx said:**
> Can I ask what you mean when you say you've been burned, what are the issues when drives are mounted under media?

I'm old and don't recall all the details. I just remember it was really bad and it is against the *File System Hierarchy Standards* for permanent media/disks to be mounted there. 

> **darskx said:**
> 
yeah, you made it pretty straight forward. O:) It does make sense, will look into renaming them.
I just left them with the names I assigned to them in windows, but these days I'm using windows less and less.
Still alot to learn, but im enjoying using linux, even for gaming.

The names used are likely the LABEL on the partition/file systems. That's usually what the automatic Gnome mounting tools do.
I didn't start our with multiple file systems under /d/.  I was mounting file systems in multiple places for media, when one day I decided to clean up the mess and plan for many disks. Media center software easily merges the different Movie and TV show sub-directories into a single library even if they are on many different disks. I know Kodi, Jellyfin, Plex all do this.  Initially, I also created slightly different named sub-directories under each mounted file system ... that too is a mistake.
/d/D1/M and /d/D1/TV
/d/D2/M and /d/D2/TV
/d/D3/M and /d/D3/TV

Would all be easier for scripting than what I did. I regret it.  I do keep music, photos, and ebooks under a single directory on 1 file system. Different disks from each other, BTW. Note how I'm saying file system and not disk.  We mount file systems.  MS-Windows mounts file systems too, not disks, not partitions. That's an important detail to grasp.

> **darskx said:**
> 
Actually that would be very helpful if you don't mind doing that.
LVM doesn't look like typical devices. The fstab lines:

```
/dev/vg00/lv-tv                    /TV     ext4 noatime,nodev,nosuid 0 1

/dev/istar-vg/lv_media             /d/D1   ext4 noatime,nodev,nosuid 0 1
/dev/istar-vg2/lv_media2           /d/D2   ext4 noatime,nodev,nosuid 0 1
/dev/istar-vg3-back/lv_media3_back /d/D3   ext4 noatime,nodev,nosuid 0 1
                                  
/dev/istar-8TB/istar-back3-a       /d/b-D1 ext4 noatime,nodev,nosuid 0 1
/dev/istar-8TB/istar-back3-b       /d/b-D2 ext4 noatime,nodev,nosuid 0 1
/dev/istar-vg2-back/lv_media2_back /d/b-D3 ext4 noatime,nodev,nosuid 0 1

/dev/WDBLK_8T/lv_d6                /d/D6 ext4 noatime,nodev,nosuid 0 1
/dev/WDBLK_8T/lv_d7                /d/D7 ext4 noatime,nodev,nosuid 0 1

/dev/istar-8TB-B/lv4_back          /d/b-D6 ext4 noatime,nodev,nosuid 0 1
/dev/istar-8TB-B/lv5_back          /d/b-D7 ext4 noatime,nodev,nosuid 0 1
```
/TV is where new TV recordings happen.  It used to be a 12 yr old Seagate 320G HDD.  Moved it to an LV on a much too large SSD.

These are all SATA or eSATA connected.

The **df -Th ***{plus a few other options to remove fake storage}* is:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB-istar--back3--a      ext4  3.6T  3.4T  236G  94% /d/b-D1
/dev/mapper/istar--8TB-istar--back3--b      ext4  3.6T  3.5T   98G  98% /d/b-D2
/dev/mapper/istar--vg2--back-lv_media2_back ext4  3.6T  3.6T   46G  99% /d/b-D3
/dev/mapper/istar--8TB--B-lv4_back          ext4  3.6T  2.8T  674G  81% /d/b-D6
/dev/mapper/istar--8TB--B-lv5_back          ext4  3.4T  954G  2.3T  30% /d/b-D7
/dev/mapper/istar--vg-lv_media              ext4  3.5T  3.4T  125G  97% /d/D1
/dev/mapper/istar--vg2-lv_media2            ext4  3.6T  3.5T   94G  98% /d/D2
/dev/mapper/istar--vg3--back-lv_media3_back ext4  3.6T  3.6T   41G  99% /d/D3
/dev/mapper/WDBLK_8T-lv_d6                  ext4  3.6T  2.8T  683G  81% /d/D6
/dev/mapper/WDBLK_8T-lv_d7                  ext4  3.6T  954G  2.5T  28% /d/D7
/dev/mapper/vg00-lv--tv                     ext4   98G   61G   33G  66% /TV
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  7.5G   12G  41% /var/lib/jellyfin

```

Gotta hate the "mapper" screwing up my lovingly crafted LVM mounts, which are /dev/{vg-name}/{lv-name} in the fstab. Learning about LVM is a prerequisite. Since LVM provides snapshotting and some advanced enterprise volume management capabilities, I like to use it.  It is better to have LVM and not need it than not to have it and need it.  Snapshots are an important part of getting clean backups.

For storage that doesn't use LVM, those device names would be a _LABEL=WD_d6_ (or something similar that I would set), not a UUID= or /dev/sdg3.  LABEL works for human beings. Much cleaner. Just ensure they are unique across all systems.

Note how I limit each file system to just 4TB? That's my maximum backup size for consistency. I do take care to have a full drive as either primary or backup storage. I don't let those mix when 8TB drives are part of the system.

---

### Post by darskx on 2024-01-04
Update: using kernel 6.6.9 I'm no longer getting Thunar crashes or the system journal spammed with;

> file ../../../gio/gfileinfo.c: line 1677 (g_file_info_get_is_symlink): should not be reached
GFileInfo created without standard::is-hidden

regards, darsk

---

