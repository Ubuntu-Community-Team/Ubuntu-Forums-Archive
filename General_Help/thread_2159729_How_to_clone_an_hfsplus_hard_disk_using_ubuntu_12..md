---
title: "How to clone an hfsplus hard disk using ubuntu 12.04"
date: 2013-07-04
forum: General Help
---

### Post by bjrnfrdnnd on 2013-07-04
Hi there, 

I am trying to clone a time machine backup hard disk from a macbook air (journalled hfsplus filesystem) using my ubuntu 12.04.

So far I managed to extract the disk image without problems using 

```
dd if=/dev/sdf of=diskimage
```

Everything seems ok, I can mount the image

```
sudo mount -o loop -t hfsplus diskimage mountpointfordiskimage

```
So far everything works perfectly. 

I do want to clone this disk though, So I am plugging in a new hard disk, erasing everything using fdisk (just to be on the safe side), and then

```
dd if=diskimage of=/dev/sdf

```
Everything seems to be fine, but I cannot mount the hard disk.

fdisk does not see any partitions, nor does gparted.

I THOUGHT that dd copies everything, including partition tables. This seems to be wrong. 

Trying to mount the disk 

```
sudo mount  -t hfsplus  /dev/sdf mountpointfordiskimage

```
results in 

```
mount: wrong fs type, bad option, bad superblock on /dev/sdf,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
as does 

```
sudo mount -o force -t hfsplus  /dev/sdf mountpointfordiskimage
sudo mount -o loop -t hfsplus  /dev/sdf mountpointfordiskimage
sudo mount -o force -o loop -t hfsplus  /dev/sdf mountpointfordiskimage

```


Trying to mount the disk results in the following log entries:

```

sudo mount -o loop -t hfsplus  diskimage mountpointfordiskimage

dmesg

[103357.622861] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

sudo mount -t hfsplus  /dev/sdf mountpointfordiskimage

dmesg 

[103464.475052] hfs: invalid secondary volume header
[103464.475056] hfs: unable to find HFS+ superblock


```

What can I do in order to copy the working diskimage to my new hard disk such that the resulting disk is a working hfsplus filesystem that can be mounted on linux and mac and can 
be read and written on mac?

---

### Post by HermanAB on 2013-07-04
Try:
dd if=diskimage of=/dev/sdf; sync

---

### Post by bjrnfrdnnd on 2013-07-04
Thanks for the hint.

Is there a website somewhere that would explain why that might work?
And is there a way to do this sync thing now even though I finished the dd process several hours ago and unplugged and replugged the external disk (the dd process takes about 24 hours...).

---

### Post by sampayu on 2014-02-06
**Addendum**:

On Linux, _if_ you can plug in both disks at the same time (I'll assume that you can do it and have /dev/sdf and /dev/sdg, being sdf your "source disk" and sdg your "destination disk"), you can **dd** straight from sdf to sdg:

```
sudo dd if=/dev/sdf bs=4M conv=sync,noerror | pv -s 500G | dd of=/dev/sdg bs=4M
```

(the command above assumes that sdf is a 500GB disk and that the size of sdg is at least 500GB)

In case **pv** isn't installed, install it by simply typing:

```
sudo apt-get install pv
```

..and then dd as mentioned before. The pv command, used between pipes, will provide you real-time info about the progress of the data transfer.

In case these disks have different physical sizes (the clone disk obviously being bigger than the cloned one), well... OSX doesn't know how to deal with a partition table that says that it is smaller than the actual physical size of the (clone) disk. Because of it, although the clone disk (sdg) will boot OSX, you won't be able to use it's remaining free space and OSX Disk Utility will return you an error if you try to use it to expand the partition in order to use that free space.

To fix this problem, you have to go back to Linux and run parted from the terminal:

```
sudo parted /dev/sdg
```

Now type **print** and hit enter. You'll get something like this (the **bold** text is the command that you gotta provide to parted, and the ***** string represents an integer number whose value will depend on how much free physical disk space is available after the end of the partition):

[I]Error: The backup GPT table is not at the end of the disk, as it should be. This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?
Fix/Ignore/Cancel?[/I] **Fix**
*Warning: Not all of the space available to /dev/sdg appears to be used, you can fix the GPT to use all of the space (an extra *** blocks) or continue with the current setting?*
*Fix/Ignore?* [B]Fix

[/B]After doing this, parted will print again the partition table for /dev/sdg and then you'll see the partition table. Run **quit** to exit parted, then plug the clone disk back into your Mac and boot OSX, go to Disk Utility and resize the partition. Now you're good to go.

---

