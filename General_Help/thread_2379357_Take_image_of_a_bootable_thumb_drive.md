---
title: "Take image of a bootable thumb drive?"
date: 2017-12-04
forum: General Help
---

### Post by etmegabyte on 2017-12-04
Hello,

I have a couple of thumb drives that I would like to take an image of.  The reason is that if I lose the thumb drive, I want to be able to put the image on a new one.  Here's the rub, though...  A couple of the drives only have like 3-4Gb of data on them, but they're on 32Gb drives.  I really don't want to use dd to make an image of the drives because it will make a 32Gb file, and while space isn't a huge issue, I'd also like the ability to put it on a smaller thumb drive in the future...

I'm running Kubuntu 17.10, if it matters...  Which it shouldn't...

Any ideas?

-ET

---

### Post by oldfred on 2017-12-04
If I have 32 or 64GB flash drives, I usually put a full install of Ubuntu (not installer) in a somewhat smaller 16GB / (root) partition and leave the rest for data. Then I rsync data from HDD regularly to data partition on my flash drives as part of my backup. Real backup is written to DVD so I have an older copy of file available just in case.
But then I can do another full install, if I need to or want the newer version of Ubuntu, but keep same data.

---

### Post by yancek on 2017-12-04
If you have an installed system on the flash drive, you can install Systemback or Pinguy Builder which will have an option to create a bootable iso of the installed system.  Either should work with Kubuntu although I expect you would need to first install the Ubiquity installer (I believe Kubuntu uses that?).  If you don't need the installer then you would just select the option to create the iso.  I'm not sure it is going to be a hybrid so dd may not work or you would need to make it hybrid. Try dd first.   isohybrid kubuntu.iso should do that although you may have to install isohybrid first.

Not sure from your post if you have an actual install or a Live usb, I've never tried it on a Live system so I'm not sure it would work.

---

### Post by etmegabyte on 2017-12-04
Sorry, I wasn't clear enough.  I'm not trying to back up my linux  system.  I'm trying to take an image of just a regular flash drive,  which normally isn't a big deal, except the flash drives in question  happen to be bootable, and I would like the image to contain that  bootability, so if I have to put it on another flash drive in the  future, the future flash drive will also be bootable...

Basically I want to take a bootable 32Gb flash drive, which has like 4Gb of data on it, and make a 4Gb bootable iso out of it.

-ET

---

### Post by C.S.Cameron on 2017-12-04
3 to 4 GB of data sounds like you are using some Persistent drives.
If so you can just save the casper-rw file, it is the only difference between a Live and Persistent USB, (besides for the word persistent in a syslinux file).
If you need to restore one of the drives you can do a new persistent install of the OS with minimum persistence and then overwrite the new casper-rw with the old.

If you are using mkusb to make your persistent drives, casper-rw is a partition not a file.
In this case you can use GParted to cut and paste the persistent partition from drive to drive.

---

### Post by VMC on 2017-12-04
Is your usb flash drive file system fat32? Also is the bootable drive made from syslinux? You can tell by looking for a ldlinux file.

---

### Post by etmegabyte on 2017-12-04
No, the two flash drives in particular are 'doze bootables.  One is the bootable setup which includes the usb drivers of this brand new machine.  I need to boot from it to run the windows 7 (which is my preferred windows version) installer if I need to ijnstall Win7 on this machine.  The second flash drive in question is a bootable flash drive made by Norton Ghost, which is also a 'doze-ish bootable.

I believe both are FAT32.

-ET

---

### Post by etmegabyte on 2017-12-04
I just had an idea but I'm not sure if it's feasible or not...  What about going at it from a different direction...  Using a piece of software to basically defrag the usb disk, moving all the data to the physical beginning of the disk, then somehow getting a block count of how many blocks actually contain data, then using the dd command and telling it to copy x number of blocks into the new iso file...  Would that work?

Something like this:
> dd if=/dev/sdc of=/path/to/new/iso.iso bs=512 count=xxx

Would this work?

-ET

---

### Post by leunam12 on 2017-12-05
Use clonezila to make clones of your USB drives.

---

### Post by yancek on 2017-12-05
I had a windows 7 install usb, simply installed Grub to the MBR of the usb and copied the extracted windows files to the usb and created a menuentry in grub.cfg.  I would think that clonezilla would work but since everything you are trying to do has to do with the proprietary windows systems you would probably be better off at a windows forum.  There isn't much incentive for Linux developers to create software to use on another OS.

---

### Post by etmegabyte on 2017-12-05
See, that's why I didn't initially specify what was on the thumb drives.  I didn't want to get into a windows/linux discussion...  My goal is to take an image of a thumb drive, including the bootable part of it.  It shouldn't matter what it boots, only that it does.

I came here first because percentage-wise, most windows forum users aren't too bright.  I find that most threads go off on a tangent and can't stay on topic.  Linux type forums have generally been filled with more on-track people.

Also, I don't have a 'doze box readily available, and if I go to a windows forum, they're going to talk about windows programs...  Which doesn't really do me a whole lot of good....

-ET

---

### Post by sudodus on 2017-12-05
> **leunam12 said:**
> Use clonezila to make clones of your USB drives.

+1

I think Clonezilla will do a great job for you. It can create a **compressed image (a directory with some files) of the whole drive** (not a partition), and you can use Clonezilla to restore a cloned image from it. The image will be small, but you must restore it to a drive of at least the same size as the original one.

Clonezilla is smart enough to only copy/clone used blocks and skip free blocks (that contain no file data). Clonezilla will also clone the head end with the partition table etc (and the backup partition table at the tail end if GPT).

See this link, [http://clonezilla.org](http://clonezilla.org)

As always with backups, please **test that it works** by restoring from the image to a fresh USB drive, that is big enough.

---

### Post by yancek on 2017-12-05
> See, that's why I didn't initially specify what was on the thumb  drives.  I didn't want to get into a windows/linux discussion

It's not a Linux/windows discussion in any way except that you are asking at a Linux forum for ways to perform something on a windows system.  If you are using exclusively the software of a specific OS it would seem only logical that you use that OS to do what you want to do to modify it.  You've had clonezilla suggested to you by several members which should do the job.  Is there some particular reason why you don't want to try it? 

> Also, I don't have a 'doze box readily available, and if I go to a  windows forum, they're going to talk about windows programs...  Which  doesn't really do me a whole lot of good....


Not having a windows box available might have been useful info on your first post.  I don't understand the last part of your comment as you are trying to modify windows so why not use windows programs?!

---

### Post by Ez_Sit on 2017-12-11
> **etmegabyte said:**
> Hello,

I have a couple of thumb drives that I would like to take an image of.  The reason is that if I lose the thumb drive, I want to be able to put the image on a new one.  Here's the rub, though...  A couple of the drives only have like 3-4Gb of data on them, but they're on 32Gb drives.  I really don't want to use dd to make an image of the drives because it will make a 32Gb file, and while space isn't a huge issue, I'd also like the ability to put it on a smaller thumb drive in the future...

I'm running Kubuntu 17.10, if it matters...  Which it shouldn't...

Any ideas?

-ET

GUI way would be to use the KDE Partition Editor to copy and restore disks, point and shoot easy. If that does not work, the Gnome Disk Utility can certainly do the trick. Command line is still simple, as below

Assuming sdb is the device of your USB drive:

sudo ddrescue /dev/sdb /home/user/flash-drive.img

or

sudo dd if=/dev/sdb of=/home/user/flash-drive.img

Either should make usable bit-for-bit copies of your usb drives to image files. Restoring is just as simple:

sudo ddrescue /home/user/flash-drive.img /dev/sdb

or

sudo dd if=/home/user/flash-drive.img of=/dev/sdb

---

