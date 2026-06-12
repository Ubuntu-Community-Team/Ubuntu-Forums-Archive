---
title: "do not have permissions necessary to view contents of external USB HDD"
date: 2015-11-01
forum: General Help
---

### Post by rare HERO on 2015-11-01
Hi. I'm not sure what is going on with my external drive. My laptop isn't allowing me to view the contents. I attached a screenshot. I can paste the results from any terminal commands necessary to troubleshoot and I just need to know which commands to run, i.e. please tell me specifically so I can copy and paste.

I searched the forums but did not find anything helpful.

---

### Post by Minny on 2015-11-01
Try opening a terminal and typing "gksudo nautilus".
That should open a file manager where you have root privileges and will be able to do what you want.

---

### Post by CharlesA on 2015-11-01
> **rare HERO said:**
> Hi. I'm not sure what is going on with my external drive. My laptop isn't allowing me to view the contents. I attached a screenshot. I can paste the results from any terminal commands necessary to troubleshoot and I just need to know which commands to run, i.e. please tell me specifically so I can copy and paste.

I searched the forums but did not find anything helpful.

Have you run a SMART check on that drive? Should be able to do that from the disk utility.

As far as checking everything else, run this in a terminal please:

```
sudo mount
```
```
sudo fdisk -l
```

> **Minny said:**
> Try opening a terminal and typing "gksudo nautilus".
That should open a file manager where you have root privileges and will be able to do what you want.

I edited your post to the correct command to use for graphical applications. See here: [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by Geoffrey_Arndt on 2015-11-02
Was the drive recently formatted to ext4 ??  - - if so, it's now owned by root.

---

### Post by mastablasta on 2015-11-02
explore the chown command

sudo chown -R user:group /path/to/disk

or run nautilus as root and then go to disk, right click it and change ownership to user.

---

### Post by rare HERO on 2015-11-03
Thanks. 

```
rene@XPS-13:~$ gksudo nautilus
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
```

That doesn't work but if I try this:

```
rene@XPS-13:~$ sudo nautilus
[sudo] password for rene: 

(nautilus:3999): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Initializing nautilus-dropbox 1.6.1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

No protocol specified

** (evince:4017): WARNING **: Could not open X display
No protocol specified
error: XDG_RUNTIME_DIR not set in the environment.
Cannot parse arguments: Cannot open display: 
I/O Error: Couldn't open file '/media/rene/60Gb WD Passport/wordsearch (copy).pdf': Permission denied.
Error loading document: Error opening file: Permission denied

(nautilus:3999): GnomeDesktop-WARNING **: Unable to create loader for mime type application/pdf: Unrecognized image file format

(nautilus:3999): GnomeDesktop-WARNING **: Error creating thumbnail for file:///media/rene/60Gb%20WD%20Passport/wordsearch%20(copy).pdf: Unrecognized image file format
No protocol specified

** (evince:4059): WARNING **: Could not open X display
No protocol specified
error: XDG_RUNTIME_DIR not set in the environment.
Cannot parse arguments: Cannot open display: 
No protocol specified

** (evince:4114): WARNING **: Could not open X display
No protocol specified
error: XDG_RUNTIME_DIR not set in the environment.
Cannot parse arguments: Cannot open display: 

(nautilus:3999): GLib-CRITICAL **: Source ID 113 was not found when attempting to remove it

(nautilus:3999): GLib-CRITICAL **: Source ID 114 was not found when attempting to remove it

(nautilus:3999): GLib-CRITICAL **: Source ID 115 was not found when attempting to remove it
```

I am able to access the files and use Nautilus to change the permissions. See the attached screenshot. Honestly, I tried this before and it didn't work. I have a second drive that also had a similar issue. I will try this with that one as well. 

For now, it looks like this is resolved.

---

### Post by rare HERO on 2015-11-03
```
rene@XPS-13:~$ sudo mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=rene)
/dev/sdb1 on /media/rene/60Gb WD Passport type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc on /media/rene/Clip Jam type vfat (rw,nosuid,nodev,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
gvfsd-fuse on /home/rene/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
```

```
rene@XPS-13:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   250069679   125034839+  ee  GPT

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28f12a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   117210239    58605088+  83  Linux
Note: sector size is 1024 (not 512)

Disk /dev/sdc: 8308 MB, 8308916224 bytes
64 heads, 32 sectors/track, 3962 cylinders, total 8114176 sectors
Units = sectors of 1 * 1024 = 1024 bytes
Sector size (logical/physical): 1024 bytes / 1024 bytes
I/O size (minimum/optimal): 1024 bytes / 1024 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   778135908  1919645538  1141509631   72  Unknown
/dev/sdc2   ?   168689522  2104717761  1936028240   65  Novell Netware 386
/dev/sdc3   ?  1869881465  3805909656  1936028192   79  Unknown
/dev/sdc4   ?  2885681152  2885736650       55499    d  Unknown

Partition table entries are not in disk order

```

---

### Post by rare HERO on 2015-11-03
Filesystem type: ext3/ext4

I would have  formatted this from a different Ubuntu laptop within the last 3-6 months.

---

### Post by rare HERO on 2015-11-03
Update. I installed gksu and gparted. I used 

```
gksu gparted
```

to format the drive to FAT32 (because I intend to use the drive as a backup for a windows computer at school).

Then I noticed that, after formatting, I did not have the correct permissions.

I used

```
gksu nautilus
```

and was unable to change the permissions. See resulting screenshot.

---

### Post by bab1 on 2015-11-03
> **rare HERO said:**
> Update. I installed gksu and gparted. I used 

```
gksu gparted
```

to format the drive to FAT32 (because I intend to use the drive as a backup for a windows computer at school).

Then I noticed that, after formatting, I did not have the correct permissions.

I used

```
gksu nautilus
```

and was unable to change the permissions. See resulting screenshot.
The ownership and permissions of a FAT32 partition file systems are set when the partition is mounted.  These can't be changed thereafter.  You will have to set the mount parameters via fstab to have the ownership and permissions you want.

---

### Post by mastablasta on 2015-11-04
DO NOT use sudo for graphical applications (e.g. nautilus)!!!!

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by rare HERO on 2015-11-07
> **bab1 said:**
> The ownership and permissions of a FAT32 partition file systems are set when the partition is mounted.  These can't be changed thereafter.  You will have to set the mount parameters via fstab to have the ownership and permissions you want.

This seems like the actual issue. All of my drives are mounted with root permissions rather than associated my user account. I looked at this information on fstab ([https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")) but I think I need a little more guidance as permissions via the terminal have been challenging for me to understand. 

Can you help?

---

### Post by yancek on 2015-11-07
You can change the owner.  On newer releases of Ubuntu, additional partitions are accessible under the /media/username directory.  To give your user use the chown command.

```
sudo chown -R /media/username
```

Should give the user the permissions previously had by root.  Replace 'username' with your actual username.  The -R makes it recursive to sub-directories/files.

---

### Post by CharlesA on 2015-11-07
> **rare HERO said:**
> This seems like the actual issue. All of my drives are mounted with root permissions rather than associated my user account. I looked at this information on fstab ([https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")) but I think I need a little more guidance as permissions via the terminal have been challenging for me to understand. 

Can you help?

Can you post your current fstab file?

> **yancek said:**
> You can change the owner.  On newer releases of Ubuntu, additional partitions are accessible under the /media/username directory.  To give your user use the chown command.

```
sudo chown -R /media/username
```

Should give the user the permissions previously had by root.  Replace 'username' with your actual username.  The -R makes it recursive to sub-directories/files.

Only works on extx partitions. the OP is using FAT32.

---

