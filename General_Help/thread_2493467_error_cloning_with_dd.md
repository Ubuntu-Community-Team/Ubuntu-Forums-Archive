---
title: "error cloning with dd"
date: 2023-12-16
forum: General Help
---

### Post by asb3 on 2023-12-16
I tried to clone a partition using dd.
The source drive is a 256G internal flash drive.
The destination is a 256 USB stick
Here is the relevent output of lsblk

```
sda                 8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1              8:1    0   243M  0 part 
&#9500;&#9472;sda2              8:2    0     1K  0 part 
&#9492;&#9472;sda5              8:5    0 223.3G  0 part 
  &#9500;&#9472;ubuntu-root   253:0    0 191.6G  0 lvm  /media/ubuntu/7a420995-9611-46f9-8e1f-d177783b5794
  &#9492;&#9472;ubuntu-swap_1 253:1    0  31.7G  0 lvm  
sde                 8:64   1   231G  0 disk 
&#9492;&#9472;sde1              8:65   1   231G  0 part /media/ubuntu/USB321FD

```
I executed the command:
> dd -if=/dev/sda5 -of=/dev/sde

After running for about 15 hours, dd finished without error (I don't have the output).

I then inspected the cloned disk; the directory structure was there, but many files were missing from the bottom level directories.
For example, on the source partition (/dev/sda5) the directory
7a420995-9611-46f9-8e1f-d177783b5794/home/asb/python 
contains the files
Car.py   hello.py     Newton.py   prob1.py     split-page.py   venv
Car.py~  mymodule.py  Newton.py~  __pycache__  split-page.py~  vscode_playground.py

while in the cloned partition (/dev/sde)
the directory 
7a420995-9611-46f9-8e1f-d177783b5794/home/asb/python
exists but doesn't contain any files

---

### Post by TheFu on 2023-12-16
So, **dd** is a bad tool for this.  It fails on any error. Use **ddrescue** instead.
Your command, 
```
dd -if=/dev/sda5 -of=/dev/sde
```
is wrong. You are copying a partition to an entire storage device. That doesn't work.  Partition ----> Partition is what you need.
If you want to clone a disk, you need the partition table as well 
OR
you need to create a partition that sized at leas the same as the source with a little extra.

Additionally, the block size of the storage needs to match if you are doing a raw "blob" copy (like dd does).  Copying from a 512b sector device to a 4Kb sector device doesn't work. The physical sector sizes have to match.

OTOH, if you setup a file system that is sized enough to hold all the files from the source, you can efficiently use rsync to copy everything over, retain the directory layout, owners, groups, ACLs, xattrs and be able to re-run the mirroring over and over and over again as needed.  Use 
```
$ sudo rsync -avz {SOURCE} {TARGET}
```
That will get almost everything - the file, data, owner, group, simple permissions. If you need xattrs, you'll need to add another option.  If you want status as the mirroring runs, use --progress2 as an option.

BTW, please whenever posting terminal output, use 'code-tags' to make the columns line up correctly. Columns matter.

---

### Post by asb3 on 2023-12-16
I tried rsync and got lots of errors of the type
"Unable to copy 'some path'
The procedure also didn't finish and threw a "device full" error, which I don't understand because the target device was slightly bigger than the source device.

---

### Post by SeijiSensei on 2023-12-16
The package name for ddrescue is gddrescue (meaning GNU).

```
sudo apt install gddrescue
```

Then just run

```
sudo ddrescue /dev/sda /dev/sdb
```

or whatever the source and target devices are.

---

### Post by TheFu on 2023-12-16
> **asb3 said:**
> I tried rsync and got lots of errors of the type
"Unable to copy 'some path'
The procedure also didn't finish and threw a "device full" error, which I don't understand because the target device was slightly bigger than the source device.

rsync works on files and directories, not file systems or blobs.  Of course, you CAN use it that way, but it doesn't mean it will work as you expect or that it is a good idea.  Unix lets us do things that are less than brilliant, if it is possible, not because it is always brilliant, but because it might be brilliant .... er ... or stupid.  It doesn't know.

---

### Post by asb3 on 2023-12-18
I'm trying again using rsync. The transfer rate is impossibly slow, about 400 kB/s.  At this rate the transfer will take close to a week.

---

### Post by TheFu on 2023-12-18
> **asb3 said:**
> I'm trying again using rsync. The transfer rate is impossibly slow, about 400 kB/s.  At this rate the transfer will take close to a week.

What's the exact command?  Both sides (source and target) need to already have file systems BEFORE you start.
Slow transfer rates usually mean the hardware is slow or failing.

---

### Post by asb3 on 2023-12-18
> **TheFu said:**
> What's the exact command?  Both sides (source and target) need to already have file systems BEFORE you start.
Slow transfer rates usually mean the hardware is slow or failing.


sudo rsync -avuz 7a420995-9611-46f9-8e1f-d177783b5794 SanDisk/backup20231216 --info=progress2

7a420995-9611-46f9-8e1f-d177783b5794 is the relative path to the mount point of the source partition, and
SanDisk is the relative path to the mount point of the target USB drive.

I only invoked this command once, but there are 17 rsync processes running.

---

### Post by yancek on 2023-12-18
>  sudo rsync -avuz 7a420995-9611-46f9-8e1f-d177783b5794 SanDisk/backup20231216 --info=progress2 

In your original post you show the UUID beginning with '7a42... as mounted under /media/ubuntu so you would need to be in the /media/ubuntu directory for that to work.  Are you.  Are you doing this from the installed Ubuntu or are you using a 'live' usb?  The part above shows you are trying to copy to 'SanDisk...' but no path is shown.  Where is that mounted?  You need to have the full path to where the SanDisk flash drive is mounted which might be also under /media/ubuntu which seems like it is a 'live' system or it would not show 'ubuntu'.

---

### Post by asb3 on 2023-12-18
> **yancek said:**
> In your original post you show the UUID beginning with '7a42... as mounted under /media/ubuntu so you would need to be in the /media/ubuntu directory for that to work.  Are you.  

Yes.

> 
Are you doing this from the installed Ubuntu or are you using a 'live' usb?  

A live USB.

> 
The part above shows you are trying to copy to 'SanDisk...' but no path is shown.  Where is that mounted? 

It's mounted in /media/ubuntu

---

### Post by TheFu on 2023-12-18
We will always question the mounts without proof.

Try using absolute paths.  Also, the order of options matters, so instead of that line
```
[s]sudo rsync -avuz 7a420995-9611-46f9-8e1f-d177783b5794 SanDisk/backup20231216 --info=progress2[/s]
```
use this
```
sudo rsync     -av      --info=progress2        /media/ubuntu/7a*4/       /media/ubuntu/SanDisk/backup20231216/
```

Compression is wasted with storage mounted to the same system (i.e. not a client/server rsync).

If you gave the file system a LABEL, you wouldn't have UUIDs in mounts. Much easier for humans.
BTW, automatically mounted storage that isn't native Linux file system under /media/ will have terrible defaults and will be 30% slower than properly mounted storage.  This happens most of the time for NTFS, FAT32 and exFAT.

A good
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
with removal of unimportant mounts would help too.  I use this so much that I have an alias.

---

### Post by asb3 on 2023-12-24
I succeeded in copying the files, but it took several days. I never found out why it was so slow.
Thanks to all who helped.

---

