---
title: "Second physical disk mount point changing on reboot"
date: 2023-04-14
forum: General Help
---

### Post by zoldy2 on 2023-04-14
Hello,   I have recently installed UBUNTU on a system with 2 physical disk.   One for the operating system and one for my data.    The second disk had a mount point of /media/myuser/Data/ ...   I renamed the disk from Data to data using the disks utility.     That changed my mountpoint to /media/myuser/data1/    ...  I would unmount the disk and clear the /media/myuser/Data/ mount point.   then mount again and it was correct /media/myuser/data/ ...    however after rebooting it goes back to /media/myuser/data1/.    Worse yet I installed a USB drive and after reboot my physical disk was /media/myuser/data2/.

I assume this has to do with automatic mounting and I need to set this statically but do not know how.  

Thanks in advance

---

### Post by TheFu on 2023-04-14
If you are new to Linux, then you have much to learn about file systems, mounting, and the rules for each.

Gnome Disks isn't a good utility.  Anything mounted under /media/ in an automatic way gets put there using some rules that we can trick, but not really control.  Much depends on the file systems involved.

a) if your "data" disk is using NTFS, you have even less control.  Avoid that file system along with other non-native Linux file systems.  If you use ext4, that is normally safe, except for USB flash drives, then you'd probably want to use f2fs.
b) The LABEL placed onto the *file system* is what will determine the name of pseudo-automatic mount points.  If you want control over the exact names and mount options, you'll want to use the fstab to control the mount.  
c) Using a label like "DATA" isn't very good.  You want something that will be unique.
d) Non-native file systems like NTFS, FAT32, exFAT, are all case insensitive.  I suspect this is the issue you are seeing.

The main thing to remember is that NTFS should only be used for spinning disks and SSDs that will be physically connected to MS-Windows systems. If the access from Windows will be over a network connection, then use a native Linux file system like ZFS, ext4, or xfs.  These all support proper Unix owners, groups, ACLs, and xattrs.  This is important.

For quick help, if you post the output from these 2 commands, we can provide an fstab line to mount the drive at boot. It will need to be there always.
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint,label

```
When posting the results, use forum code-tags (see Adv Reply) or it won't be easy to read the output. Please don't make it hard to help you.

If you'd like more help, search for "ubuntu fstab" for a how-to guide.

---

### Post by zoldy2 on 2023-04-14
Hello thank you for helping me..   I am not using NTFS I am using ext4.  I am fairly new to Linux although I have a long IT background I never did much in Linux until now.   This below is after correcting it after each reboot.  

```
Filesystem      Size  Used Avail Use% Mounted ontmpfs           1.6G  2.6M  1.6G   1% /run
/dev/sdb2       234G   16G  207G   7% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/sdb1        99M  6.1M   93M   7% /boot/efi
tmpfs           1.6G   92K  1.6G   1% /run/user/1000
/dev/sdc1       932G  369G  564G  40% /media/zoldy/USB Drive
/dev/sda3       916G  211G  659G  25% /media/zoldy/data
zoldy@myserver:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type   Size  Used Avail Use% Mounted on
/dev/sdb2      ext4   234G   16G  207G   7% /
/dev/sdb1      vfat    99M  6.1M   93M   7% /boot/efi
/dev/sdc1      exfat  932G  369G  564G  40% /media/zoldy/USB Drive
/dev/sda3      ext4   916G  211G  659G  25% /media/zoldy/data
zoldy@myserver:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint,label
NAME     SIZE TYPE FSTYPE MOUNTPOINT             LABEL
sda    931.5G disk
&#9492;&#9472;sda3 931.5G part ext4   /media/zoldy/data      data
sdb    238.5G disk
&#9500;&#9472;sdb1   512M part vfat   /boot/efi
&#9492;&#9472;sdb2   238G part ext4   /
sdc    931.5G disk
&#9492;&#9472;sdc1 931.5G part exfat  /media/zoldy/USB Drive USB Drive
```

---

### Post by Dennis N on 2023-04-14
Are you mounting 'data' using the file manager or do you have an entry in /etc/fstab?

If you click to mount this data partition from the file manager, the mounting process (which uses a helper named udisks2) always makes a new folder in /media/myuser for the mount point, naming it with the file system label or its UUID. If a folder with the name already  exists, udisks2 adds '1' when naming the new folder, and you get it mounting at data1 instead of data. So, the folder for the mount point should not be manually created ahead of time when mounting this way.

---

### Post by TheFu on 2023-04-14
Add this line to your /etc/fstab. Use **sudoedit /etc/fstab** to accomplish this. Use sudoedit to modify/create and system config files.

```
LABEL=data     /media/data   ext4   nofail,errors=remount-ro      0     2
```

Be certain where ever that drive is located, if mounted, that you umount it. 
Next run **sudo mount -a** and you'll find everything under /media/data/.  You don't actually need to run that command, but admins should avoid rebooting a computer when it isn't necessary.  A reboot will see the updated fstab and mount stuff ... using the equivalent of **mount -a**.

It will be part of the automatic **fsck** runs that happen about every 60 days.  You can set that to happen at boot a little more often, if you like using **tune2fs**.  I prefer automatic fsck runs every 30 days. It is a safe thing to do for native Linux file systems. You want this.

*You can stop reading here.*

There are lots of ways to determine the file system uniquely.  LABEL is one. UUID is another.  There are others too.  I find UUIDs to be anti-human, so since you already have a label, that can be used. Just be 100% certain that no other storage device you ever connect to this system has the same label.  A USB drive could make for a terrible day, if it was connected with "data" as the label.  See why I really want you to change the existing LABEL to something less generic, but still unique?

When I chose to visit this thread, I expected you were trying to use /dev/sdXn, since lots of old examples show that.  Those device files can change at boot. It is purely a kernel discovery order and that can change based on all sorts of things we don't control.

Lastly, the fstab manpage has a description for what each field means in the fstab.  Pay special attention to the 6th field. It matters and you don't want 0 for native linux file systems.

There's little reason to have a /media/{username}/ area on Unix. It is just another layer.  Use normal Unix owner, group, and permissions to restrict access from other accounts, if you like.

---

### Post by zoldy2 on 2023-04-14
I tried your suggestion adding that line to the fstab and now the system will not boot.

Failed to active swap /swapfile
dependency failed for swaps

---

### Post by TheFu on 2023-04-14
Where did you put it?

It needed to be on a line, alone and no other line should have been touched. 
Also, add 1 blank line after it, to be safe (though this hasn't mattered in 20+ yrs).
swapfile?  Ewwww. I don't use those, but that doesn't matter.

If you boot into recovery mode or from a "Try Ubuntu" USB flash drive, then you can post the full contents of the /etc/fstab file

---

### Post by zoldy2 on 2023-04-14
I inserted exactly what you posted but when I save it it now looks like this.

I have to type this out so I left out the comment line details. 

#
#
#
#
#
#
#
LABEL=data /media/data ext4 nofail,errors=remount-ro 0 2UUID=7272fae38-6246-40f4-a451-1cfb9e58e9d6 / ext4 errors=remount-ro 0 1
#
UUID=90C8-3811 /boot/efi vfat umaks=0077 0 1 
/swapfile none wap sw 0 0

---

### Post by zoldy2 on 2023-04-14
sorry some typos in there was not ready to post.

[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]LABEL=data /media/data ext4 nofail,errors=remount-ro 0 2UUID=7272fae38-6246-40f4-a451-1cfb9e58e9d6 / ext4 errors=remount-ro 0 1[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]UUID=90C8-3811 /boot/efi vfat umaks=0077 0 1[/COLOR]
[COLOR=#000000]/swapfile none swap sw 0 0[/COLOR]

---

### Post by zoldy2 on 2023-04-14
I believe I figured out where the line break was missing.   Just rebooting now.

---

### Post by zoldy2 on 2023-04-14
okay I think this now resolved everything it changed the path from /media/myuser/data/ to /media/data/ ...  but that is fine by me.

Thank you for the help!!!

---

### Post by mIk3_08 on 2023-04-14
> **zoldy2 said:**
> okay I think this now resolved everything it changed the path from /media/myuser/data/ to /media/data/ ...  but that is fine by me.
Thank you for the help!!!
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by TheFu on 2023-04-15
> **zoldy2 said:**
> okay I think this now resolved everything it changed the path from /media/myuser/data/ to /media/data/ ...  but that is fine by me.

Thank you for the help!!!

Linux desktop systems have a number of different programs that want to manage mounts.  It is best for those locations NOT to collide, so it is best to not try to force 1 mount control solution to step on the location where another mounting tool expects to have full control.  /media/{usename} is one of those locations that only 1 program likes to control, so it appears that other mount methods are rejected to that specific location.

Really, all of /media/ is supposed to be controlled by some GUI tool and it is best to avoid it, but since Canonical limits where storage can be mounted and still accessed by snap programs (in violation of the Linux File System Hierarchy Standards), they hard coded the locations, means that practically, we users need to put extra storage under /media/ which is only supposed to be used for temporary mounts, like optical media.  Sigh.
Much of what snap packages do breaks existing standards. Whenever the snap team has this pointed out, they just push it as a problem for someone else.  For example, /home/ **is not** a mandated standard.  HOME directories should be allowed elsewhere.  Snaps won't work if your HOME directory isn't in /home/{username}/. Broken by design.

---

