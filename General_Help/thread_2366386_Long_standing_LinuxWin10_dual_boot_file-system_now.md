---
title: "Long standing Linux/Win10 dual boot file-system now appears warped!"
date: 2017-07-17
forum: General Help
---

### Post by makem2 on 2017-07-17
On Install I started with:

1. Xubuntu, a separate /home and a /data (ext4) partition on an SSD
2. Windows 10 with a separate data partition in which was my Win10 profile on the original HD.

Currently:
```

makem@ssdTOSH:~$ sudo fdisk -l
[sudo] password for makem: 
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9EFB600C-A9FF-4A05-863B-84E383D8B32F


Device         Start       End   Sectors  Size Type
/dev/sda1       2048    487423    485376  237M EFI System
/dev/sda2     487424  40486911  39999488 19.1G Linux filesystem
/dev/sda3   40486912 240486399 199999488 95.4G Linux filesystem
/dev/sda4  240486400 244486143   3999744  1.9G Linux swap
/dev/sda5  244486144 468860927 224374784  107G Linux filesystem




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C79D48CD-4D4D-4DAA-A116-0A83EBA9B7EC


Device          Start        End    Sectors   Size Type
/dev/sdb1        2048    2099199    2097152     1G Windows recovery environment
/dev/sdb2     2099200    2303999     204800   100M EFI System
/dev/sdb3     2304000    2566143     262144   128M Microsoft reserved
/dev/sdb4     2566144  161426955  158860812  75.8G Microsoft basic data
/dev/sdb5   161427456 1914398719 1752971264 835.9G Microsoft basic data
/dev/sdb6  1926705152 1927682047     976896   477M Windows recovery environment
/dev/sdb7  1927682048 1953523711   25841664  12.3G Windows recovery environment
makem@ssdTOSH:~$

```

sda
[IMG]https://pasteboard.co/GBmKUKD.png[/IMG]

sdb
[IMG]https://pasteboard.co/GBmMvzj.png[/IMG]

Everything appears to be working fine except what I see in file manager:

1. I notice that what was the original folder 'Data' is now mounted at /media/makem/Data1/. The permissions of the contained files are correct.

2. The folder WinData, mounted at /media/makem/ now contains a Data1 folder which contains the files mentioned above. In addition there is a a Data folder which contains a large number of files all owned by root. However even though the permissions are blanked I can still read and write to the folder.

I cannot understand where the mount point Data1 came from and why all WinData files are owned by root.

---

### Post by oldfred on 2017-07-17
Windows formats do not support Linux owership and permissions. So a set of default settings is used when you mount any Windows partition. They always seem to mount with root & work as you have permissions.
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion. 
Are you mounting the NTFS with fstab into /media. Nautilus, not sure if your file browser in Xubuntu is similar or not, then often tries to auto mount and since it can only be mounted once, you get a second mount shown that does not work. Did you label partition "Data" so that is default Naulitus mount?



With Window 10 you must make sure Windows fast start up or always on hibernation is off. And updates in Windows will probably turn that back on. It in effect locks up all NTFS partitions and then Linux can only see them read only, but default mounts are normally read/write, so do not work.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by makem2 on 2017-07-17
Thanks for the quick reply.

This is my fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


UUID=17b75597-508d-4e0d-a6fc-0a138af1c7ff /               ext4   noatime,nodiratime,errors=remount-ro 0       1


UUID=CCBC-12A0  /boot/efi       vfat    defaults        0       1


UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4   noatime,defaults        0       2


UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0       0


UUID=3c47fe2c-04d9-4da3-9ce6-725200e1c14f none            swap    sw              0       0




tmpfs    /media/ramdisk tmpfs   nodev,nosuid,noexec,nodiratime,size=3072M   0 0


#256ssd
UUID=871081ad-6b46-44bb-ae44-bce1a8611061 /media/makem/256ssd ext4 nofail,noatime,defaults 0 2


#windata
UUID=D232DC8B32DC75C7  /media/makem ntfs noatime,defaults        0       2


#Data UUID=b15b5fdc-a6ee-4fd9-add9-1039d86dfee2 /media/makem ntfs noatime,defaults        0       3

```

---

### Post by Dennis N on 2017-07-17
If you mount a partition with file system label Data in the file manager (which uses udisks2, not mount), it creates a mount point at /media/username/Data.  If /media/username/Data already exists, then it creates a new mount point /media/username/Data1

Usually mount point made by udisks2 is deleted when unmounted, but could be left behind by something like improper shutdown.

Example: Existing directory with name Data. 
```
dmn@Roxanne:/media/dmn$ tree -L 1
.
&#9492;&#9472;&#9472; Data

1 directory, 0 files

```
after mounting partition (file system) with same name (Data) in file manager with udisks2:
```
 
dmn@Roxanne:/media/dmn$ tree -L 1
.
&#9500;&#9472;&#9472; Data
&#9492;&#9472;&#9472; Data1

2 directories, 0 files

```

There you have it.

---

### Post by oldfred on 2017-07-17
/media/makem/256ssd
/media/makem 

Your second mount will erase the first mount. Use something like /media/makem/win_data

I have my data partition in /mnt/data, as well as several other temporary mounts. I was testing instructions on using /mnt and it wiped out all my other mounts in /mnt.

---

### Post by makem2 on 2017-07-17
I have remembered that ssd was an external drive used temporarily.

```

makem@ssdTOSH:~$ sudo blkid
/dev/sda1: UUID="CCBC-12A0" TYPE="vfat" PARTUUID="0ca21933-62a8-4dbd-aa0e-d484ee6d028c"
/dev/sda2: UUID="17b75597-508d-4e0d-a6fc-0a138af1c7ff" TYPE="ext4" PARTUUID="69d7a9ce-68dc-4ccd-aeb8-fed18280e943"
/dev/sda3: UUID="d78428d2-66ad-474b-a7bc-8144945dd6a1" TYPE="ext4" PARTUUID="1f4ce6eb-f591-4bfc-9418-a11129872523"
/dev/sda4: UUID="68342eb5-6386-48f4-a2ef-e1683ff58be5" TYPE="swap" PARTUUID="909ad8de-771f-4fc3-9e5e-f8326810066d"
/dev/sda5: LABEL="Data" UUID="b15b5fdc-a6ee-4fd9-add9-1039d86dfee2" TYPE="ext4" PARTUUID="bbb3e9e7-0f4f-49e9-b56e-967c2b21798f"
/dev/sdb1: LABEL="WinRE" UUID="D8AC6421AC63F880" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="294fe5c5-7b1f-48fc-b9dd-c92842250842"
/dev/sdb2: LABEL="ESP" UUID="0A66-6E5B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="e5a1951b-f090-441d-92ce-dbe518417005"
/dev/sdb3: UUID="11A8-6C10" TYPE="vfat" PARTLABEL="Microsoft reserved partition" PARTUUID="35435f1b-40ab-4a92-a704-01f2aa69d2f4"
/dev/sdb4: LABEL="Win10" UUID="BC9A68789A683156" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1db6050f-d9c9-424a-b92f-0b4a61ccee46"
/dev/sdb5: LABEL="WinData" UUID="D232DC8B32DC75C7" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1d91cc7e-4481-4169-9117-c5b947315241"
/dev/sdb6: UUID="387E1FA37E1F5948" TYPE="ntfs" PARTUUID="699c6fd9-8fe5-43fa-925b-f1c20edc794d"
/dev/sdb7: LABEL="Recovery" UUID="8E5C69F15C69D50D" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9fefe4de-9237-44f0-85a2-829a76543f36"
makem@ssdTOSH:~$ 

```

EDIT: I changed the '[COLOR=#000000][FONT=&amp]UUID=D232DC8B32DC75C7  /media/makem ntfs noatime,defaults        0       2'

[/FONT][/COLOR]To: [COLOR=#000000][FONT=&amp]UUID=D232DC8B32DC75C7  /media/makem/win_data ntfs noatime,defaults        0       2

Rebooted and now have separate 'data's thanks. However (there is always a however?) at startup it went off checking the filesystem for a couple of minutes.[/FONT][/COLOR]

---

### Post by makem2 on 2017-07-17
> **Dennis N said:**
> If you mount a partition with file system label Data in the file manager (which uses udisks2, not mount), it creates a mount point at /media/username/Data.  If /media/username/Data already exists, then it creates a new mount point /media/username/Data1

Usually mount point made by udisks2 is deleted when unmounted, but could be left behind by something like improper shutdown.

Example: Existing directory with name Data. 
```
dmn@Roxanne:/media/dmn$ tree -L 1
.
&#9492;&#9472;&#9472; Data

1 directory, 0 files

```
after mounting partition (file system) with same name (Data) in file manager with udisks2:
```
 
dmn@Roxanne:/media/dmn$ tree -L 1
.
&#9500;&#9472;&#9472; Data
&#9492;&#9472;&#9472; Data1

2 directories, 0 files

```

There you have it.

I did have a couple of improper shutdowns and had a feeling the changes took place then but I have lived with it for a while now.

---

### Post by makem2 on 2017-07-17
This is not right?

```

makem@ssdTOSH:~$ cd /media/makem
makem@ssdTOSH:/media/makem$ ls -la
total 32
drwxr-x---+ 8 root  root  4096 Jul 17 20:00 .
drwxr-xr-x  4 root  root  4096 Apr 21 23:27 ..
drwx------  2 root  root  4096 Apr 20 21:44 a251d4c3-7ede-415f-a17b-4524a2b4a87e
drwx------  2 root  root  4096 Apr 20 22:28 a251d4c3-7ede-415f-a17b-4524a2b4a87e1
drwx------  2 root  root  4096 Apr 20 21:37 Data
drwxr-xr-x  4 makem makem 4096 Jul 16 23:32 Data1
drwxrwxrwx  1 root  root  4096 Jul 17 19:07 win_data
drwx------  2 root  root  4096 Apr 20 21:31 WinData
makem@ssdTOSH:/media/makem$

```

Does this explain why it always now checks the filesystem?

---

### Post by oldfred on 2017-07-17
Does this UUID exist? I do not see it in your list.
But you again have it shown twice as second as a 1 at end?
a251d4c3-7ede-415f-a17b-4524a2b4a87e

If just old mount points you can delete them.

And I notice you labeled partition Windata, but mounted as win_data. That is ok, just do not confuse them.
but I once used Data as label and data as mount point and got confused on which was which.
I still use labels, but try to make them enough different from mount points that I do not use wrong one.

---

### Post by makem2 on 2017-07-17
I put the fstab back to what it was initially in this thread because of the above result. Now I get this:

```

makem@ssdTOSH:~$ cd /media/makem
makem@ssdTOSH:/media/makem$ ls -la
total 20
drwxrwxrwx 1 root root 4096 Jul 17 21:19 .
drwxr-xr-x 4 root root 4096 Apr 21 23:27 ..
drwxrwxrwx 1 root root 4096 Jul 17 15:06 Data
drwxrwxrwx 1 root root    0 Oct 29  2016 MSOCache
drwxrwxrwx 1 root root    0 Sep  7  2015 $RECYCLE.BIN
drwxrwxrwx 1 root root 4096 Mar 18 10:52 System Volume Information
drwxrwxrwx 1 root root    0 Oct 27  2015 .Trash-1000
drwxrwxrwx 1 root root 4096 Jun 25  2016 windows

```

But all are still accessible. I am totally lost here. Can anyone sort out what I should have in the fstab?

All I need is /; /home; /data and windows10 with a data partition.

---

### Post by makem2 on 2017-07-17
> **oldfred said:**
> Does this UUID exist? I do not see it in your list.
But you again have it shown twice as second as a 1 at end?
a251d4c3-7ede-415f-a17b-4524a2b4a87e

If just old mount points you can delete them.

And I notice you labeled partition Windata, but mounted as win_data. That is ok, just do not confuse them.
but I once used Data as label and data as mount point and got confused on which was which.
I still use labels, but try to make them enough different from mount points that I do not use wrong one.

I cannot see it in the above blkid. It appears to have appeared and follows the format of data, data1 ie each is duplicated with a '1' at the end of the last one.

EDIT: It is not in the fstab.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>


UUID=17b75597-508d-4e0d-a6fc-0a138af1c7ff /               ext4   noatime,nodiratime,errors=remount-ro 0       1


UUID=CCBC-12A0  /boot/efi       vfat    defaults        0       1


UUID=d78428d2-66ad-474b-a7bc-8144945dd6a1 /home           ext4   noatime,defaults        0       2


UUID=68342eb5-6386-48f4-a2ef-e1683ff58be5 none            swap    sw              0       0


UUID=3c47fe2c-04d9-4da3-9ce6-725200e1c14f none            swap    sw              0       0




tmpfs    /media/ramdisk tmpfs   nodev,nosuid,noexec,nodiratime,size=3072M   0 0


#256ssd
#UUID=871081ad-6b46-44bb-ae44-bce1a8611061 /media/makem/256ssd ext4 nofail,noatime,defaults 0 2


#windata
UUID=D232DC8B32DC75C7  /media/makem ntfs noatime,defaults        0       2


#Data UUID=b15b5fdc-a6ee-4fd9-add9-1039d86dfee2 /media/makem ntfs noatime,defaults        0       3

```

---

### Post by oldfred on 2017-07-17
Then not an issue, you can delete obsolete mount points if desired.

---

### Post by makem2 on 2017-07-17
> **oldfred said:**
> Then not an issue, you can delete obsolete mount points if desired.

I appreciate that but have no idea where they came from. They were not there at the start of this thread.

I gather that one problem I have is that the partitions should not be mounted /media/makem/xxxx but instead should be /media/xxxx. However, it will mess up all paths set up currently in software.

Would it be easier in the long run to re-install Xubuntu as /home is separate?

---

### Post by oldfred on 2017-07-17
Several versions ago they change default mounts from /media to /media/$USER.
I think that was so each user has his own mount for security reasons.

Having a separate /home would not change that.

But you can create /home as separate partition without re-installing.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by makem2 on 2017-07-17
So /media/makem/xxxx is correct. Thank you.

I already have a separate /home partition and thought I could reinstall to re-set everything as I had read that the 'Flavour' could be changed easily when a separate /home partition was used.

Would a re-install fix the fstab issues?

---

### Post by oldfred on 2017-07-17
A reinstall only adds the default fstab entries. Any other mounts you have to manually recreate. Why I used to backup fstab. I now script an update to fstab as part of every new install script.

I prefer to install another version if just experimenting in another 25GB / (root) partition. I do not use separate /home as that also includes user settings which may or may not conflict with settings in another install. So I use /mnt/data for most of data normally in /home and can then mount that into every install. And /home is then tiny, so I leave in inside / (root) partition.

---

