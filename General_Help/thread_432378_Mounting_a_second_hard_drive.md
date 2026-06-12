---
title: "Mounting a second hard drive"
date: 2007-05-03
forum: General Help
---

### Post by woopud on 2007-05-03
Just installed a fresh 7.04 on my Master hd but I still have a slave hd in the same pc which contains a lot of files I need, how do I get Ubuntu to automatically mount it at startup ?  I see the drive when I do sudo fdisk -l  The slave hd contains a 6.10 installation, just want to get the files and then format it.

Bert

---

### Post by jfinkels on 2007-05-03
> **woopud said:**
> Just installed a fresh 7.04 on my Master hd but I still have a slave hd in the same pc which contains a lot of files I need, how do I get Ubuntu to automatically mount it at startup ?  I see the drive when I do sudo fdisk -l  The slave hd contains a 6.10 installation, just want to get the files and then format it.

Bert

You're going to have to edit your /etc/fstab file by adding a line for the hard drive. Type ```
man fstab
``` for more info on fstab. You're going to need to know the filesystem, the device name, and some other options (which I am not too keen on because I'm not an expert with /etc/fstab).

---

### Post by benanzo on 2007-05-03
depending on what the drive is formatted as, I assume ext3 since you said it has an old edgy installed on it:

make a folder for it to mount into

```
sudo mkdir /mnt/other_disk
```

then mount it:

```
sudo mount -t ext3 /dev/sda1 /mnt/other_disk
```

"mount" is the command to mount a filesystem
"-t ext3" is the flag for "type" in this case ext3.  If it's a fat32 partition use vfat.
"/dev/sda1" is the device.  Your's will most likely be different than sda1.
"/mnt/other_disk" is where you want it to mount to.

If you want to mount it permanently just add this line to your /etc/fstab

```
/dev/sda1 /mnt/other_disk ext3 defaults 0 0
```

changing the device and type accordingly

---

### Post by drlisacuddy on 2007-05-04
There are two ways to mount an HD:

1) use the disk manager that comes with your Ubuntu/Kubuntu distro

2) manually edit your fstab file.

I recommend the disk manager, just select your drive and tell Ubuntu to mount it at a folder in the media folder (make a new one if you need to.)

If the disk manager doesn't work (and it should) then you should open a terminal. You need to know the name of your drive (the internal name, like hdd1 or hdd0) and a few commands.

In GNOME enter this at the terminal:

```
sudo gedit /etc/fstab 
```

In KDE replace gedit with kate.

The editor should open. The first column is your device address; it's usually /dev/hdd0 or something like that. Here you should type 
```
/dev/<device name>
```

then press TAB.

The second column is the mount point - this is where Ubuntu mounts your drive and this is where you see your files. Here type:

```
/media/<folder name>
```

<folder name> must exist.

The third column is your hard drive filesystem - for windows, it's "vfat" for FAT drives, ntfs for NTFS drives, for Ubuntu formatted drives it's usually ext3. Type what the hard drive's filesystem is. If you don't know type "auto" and ubuntu will figure it out.

The fourth column is your options. Here you want to type "auto" followed by a comma, followed by "user" so that it mounts at startup (auto) and anybody can mount (user).

The fifth and sixth columns should be both 0. You probably don't want to back it up or have fsck check it.

Hope this helps! I understand your problem, when I had Ubuntu I had to do this because my main windows drive wouldn't mount and disk manager didn't work. If you have problems just reply and I'll figure it out for you.

---

### Post by skathrein on 2007-05-04
Do you know the filetype?  Such as whether its ntfs, fat, ext3, etc?

---

### Post by woopud on 2007-05-04
```
woopud@woopud-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9777    78533721   83  Linux
/dev/hda2            9778        9964     1502077+   5  Extended
/dev/hda5            9778        9964     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3495    28073556   83  Linux
/dev/hdb2            3496        3647     1220940    5  Extended
/dev/hdb5            3496        3647     1220908+  82  Linux swap / Solaris
woopud@woopud-desktop:~$ 



```


Bert

---

### Post by skathrein on 2007-05-04
I would agree with Benanzo and the other posts above since it looks like it has the ext3 filesystem.  However, I would mount it to the /media directory.  I have a second hard drive and edit fstab as stated below to mount it.  You need to make a directory using a name for the hard drive.  I'll assume you will call it "Second."  If you call it something else, just substitute that name wherever you see "Second" below.  Run the following commands:
```
sudo mkdir /media/Second
sudo gedit /etc/fstab
```

Now, at the end of your fstab file, add the following by following the format of the entries already there (this is assuming you don't already have an entry for /dev/hdb1):
```
/dev/hdb1     /media/Second     ext3     defaults     0     0
```

Then save the fstab file and close it.  Next run the following command to see if it mounts:
```
sudo mount -a
```

After it's mounted, run chmod to change the permissions if needed.  For example, to change all permissions to read/write/execute, type:
```
sudo chmod -R 777 /media/Second 
```

---

### Post by woopud on 2007-05-05
Somehow after the latest updates it mounted automatically.
Thanks for all the replies though.

Bert

---

