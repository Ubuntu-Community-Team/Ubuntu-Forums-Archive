---
title: "Saving factory state of a laptop"
date: 2014-03-17
forum: General Help
---

### Post by spacemen12 on 2014-03-17
Hi,
    I would like to know how to save the factory state of the laptop. They don't come with cd or dvd anymore.

    My current way of doing it is:
1. out of the box
2. run ubuntu on a usb stick (never boot from disk)
3. plug in an external hard drive
4. dd the /dev/sda of the internal disk to the external hard drive.
5. Install linux on the hard drive

    It works, but for an internal drive of 350gb, it makes a 350gb files. 

    Is there a better way to save the initial state (in order to put it back as necessary): partitioning, files, etc.

Best regards,

---

### Post by MartyBuntu on 2014-03-17
You can make a complete drive backup with any number of utilities like Clonezilla, Redo, Acronis Tru Image etc...then store the backup on an external drive.

---

### Post by lisati on 2014-03-17
The last two laptops I've purchased came with software preinstalled that let me make recovery disks.

---

### Post by rollingthunderb on 2014-03-17
> **lisati said:**
> The last two laptops I've purchased came with software preinstalled that let me make recovery disks.

Ditto for me.

Another way I've done this for people with laptops that want an escape hatch if they don't like 'nix is some laptops I've found have a recovery partition with a special "Fkey (Like F12)" that sends them to factory default mode. I leave that in place and just "trick" (not really) linux to install "along side" of the windows install even when it isn't really there. 

Here's the general idea;

sda0=boot partition
sda1=recovery partition (typically 4 Gb or so) - Leave alone
sda2=Linux installed on what was the "Window's C: drive"
Use gparted are some other way to format this drive to remove the windows install.

Be careful doing all of this obviously.

---

### Post by oldfred on 2014-03-17
This is for HP, other vendors may be similar but not identical.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01867418&cc=us&dlc=en&lc=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01867418&cc=us&dlc=en&lc=en)

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

One user posted his method was to just remove hard drive even before booting system. Then he buys a new SSD to install Ubuntu into and make it fast. Later when he sells system he reinstalls Windows drive and can sell it with a "new" Windows.

---

### Post by tripp98 on 2014-03-17
Second post #5.  Most manufacturers will not support other OS's besides the one that it was purchased with.  Save the original hard drive with original OS and purchase bigger/faster drive and install other OS.  If you have any problem swap hard drives back to original and warranty will be much easier.

---

### Post by spacemen12 on 2014-03-18
This somehow the intention, but I don't like the idea of having a 500gb or 1tb drive collecting dust in a closet. I would rather have the ability to restore the data originally on the disk, and using the disk for storage.

I am looking at clonezilla and I find two contradicting info on their web site front page [http://clonezilla.org/](http://clonezilla.org/)
1. "Clonezilla saves and restores only used blocks in the harddisk. " (from the description at the top)
2. "The destination partition must be equal or larger than the source one." (in the limitations)

From the 1st citation if there is 8gb of stuff, the backup should take 8gb, but from citation 2 if those 8gb are on a 500gb drive the backup will take 500gb. Can someone clarify this for me?

---

### Post by oldfred on 2014-03-18
I do not know for sure, but it would seem clonezilla is just compressing data. 
Not sure if it then restores to all the locations on drive. Linux does not store data at 'front' of drive like Windows but data may be anywhere on the 500GB. Or it expect internal partition data to be the same. 

The old dd command literally copies all the empty space so in your example dd would copy 500GB of "data" even though only 8GB was real data.

---

### Post by efflandt on 2014-03-19
Computers without backup disks should include some utility to create recovery and/or utility or driver disks.

Some drive manufacturers (like WD for their drives and Seagate for Seagate or Maxtor drives) have a free version of Acronis which I first found useful when clonezilla stopped dead in its tracks when it got to a section of bad sectors it could not read while attempting to image a failing laptop drive. For the free version to work at least 1 drive on the computer (internal or external) has to be from that manufacturer. Besides the usual sector by sector imaging, Acronis can instead do an image file by file, which as long as you have repaired a failing drive, just reads parts of the partitions that have files, not even trying to read bad sectors. That also makes a smaller image because it it only images the data, and not empty or bad sectors nor locking out what were bad sectors on previous drive. While you write partitions back to a drive, you can easily expand any of them if you want to.

I also used Acronis when the Linux partition at the far end of the 3 year old drive on my desktop began failing. Since only the far end of the drive was failing, which did not affect the Windows partitions, I used Acronis to image them and the Windows MBR (grub is on a different drive) after shrinking the Windows OS partition (needed more room for Linux Steam games). I installed Ubuntu fresh following that and copied over my /home from the old drive. The only thing corrupted was some Steam game files and Steam checking game files was able to replace the few files that were corrupted. So I was back up and running with larger Linux partition like nothing happened.

---

### Post by mastablasta on 2014-03-19
> **spacemen12 said:**
> This somehow the intention, but I don't like the idea of having a 500gb or 1tb drive collecting dust in a closet. I would rather have the ability to restore the data originally on the disk, and using the disk for storage.

I am looking at clonezilla and I find two contradicting info on their web site front page [http://clonezilla.org/](http://clonezilla.org/)
1. "Clonezilla saves and restores only used blocks in the harddisk. " (from the description at the top)
2. "The destination partition must be equal or larger than the source one." (in the limitations)

From the 1st citation if there is 8gb of stuff, the backup should take 8gb, but from citation 2 if those 8gb are on a 500gb drive the backup will take 500gb. Can someone clarify this for me?

second one refers to restore. when you restore the compressed image the partition you are restoring to must be equal size or larger. backup won't take 500 GB, but when you are restoring it you will have to restore it to 500 GB hard drive or larger.

also have a look at redobackup. i find it has a nicer interface than clonezilla and does more or less same thing. problme i had with clonezilla is the options are not really explained when you are doing things and there is no way to go back in menu. so if you change your mind while setting up the backup you need to do it all over agian. i guess if oyu are used to it you will do it right the first time and this is not an issue. but for me when i started it was. took me three times through all menues before it continued.

---

### Post by sudodus on 2014-03-19
> **mastablasta said:**
> second one refers to restore. when you restore the compressed image the partition you are restoring to must be equal size or larger. backup won't take 500 GB, but when you are restoring it you will have to restore it to 500 GB hard drive or larger.
+1

The compressed image by ***Clonezilla*** can be quite small, but when you intend to restore it, you need a drive of the same size as the source drive of larger.

> 

also have a look at redobackup. i find it has a nicer interface than clonezilla and does more or less same thing. problme i had with clonezilla is the options are not really explained when you are doing things and there is no way to go back in menu. so if you change your mind while setting up the backup you need to do it all over agian. i guess if oyu are used to it you will do it right the first time and this is not an issue. but for me when i started it was. took me three times through all menues before it continued.

I like Clonezilla, and I have not tried redobackup. I suggest you try a couple of tools, and use the one you like best. You can even pipe the output of dd to a file compression program and reduce the size of the image, similar to what Clonezilla does, but not as efficiently.

```

sudo -s
dd if=/dev/sdx bs=4096 | gzip > dd-sdx.img.gz
sync
exit

```
or slower but ~20% better compression
```

sudo -s
dd if=/dev/sdx bs=4096 | xz > dd-sdx.img.xz
sync
exit

```

where x is the source drive, a for the first one. [mkusb]("http://ubuntuforums.org/showthread.php?t=1958073") can be used to restore safely from a compressed image file **[FONT=courier new]dd-sdx.img.gz[/FONT]** or **[FONT=courier new]dd-sdx.img.xz[/FONT]**

If you want to be 100% sure, get a new drive of the same size of larger, and test that restoring from the backup really works.

My recommendation: Learn Clonezilla and use it. Test that restoring from the backup really works.

---

### Post by spacemen12 on 2014-03-21
Great, Clonezilla works great.

Now I have a followup question. For the drive that I dd (several months ago), my iso file is 360gb, but there is probably 10gb on info on it. Is there a way to mount that iso file in clonezilla and then do the colnezilla copying process on the mounted 360gb iso file.

In short.
1. Plug in externalDriveA to the laptop
2. Start clonezila on laptop
3. Mount the 360gb iso file on the laptop (lets name it d1). Remember d1 is a drive with many (3-ish) partitions.
4. run clonezilla with the source being d1

I wonder how to do step 3 and 4.

Thanks!

---

### Post by sudodus on 2014-03-21
It is possible but not easy. Knowing the offset from the drive head to each of the partitions you can loop mount the partitions one at a time. But I would not recommend it. If you want to compress the information there are two ways:

1. Compress the big image file

```
gzip -c d1 > d1.gz
```

To make it really small, you should also zeroise the free space, but the methods I know requires mounting the partitions.

2. Flash it to a drive, and use Clonezilla on that drive. It means that you need a separate drive of at least the same size, 360 GB, that will be completely overwritten. That drive can be used for other things afterwards, so it is not wasted.

I would recommend method 2. Maybe it looks awkward, but it will make things easier in the future.

---

### Post by Mark Phelps on 2014-03-21
Regarding whether or not you can mount the Clonezilla image file, this is from the Clonezilla website, under Limitations:

> Due to the image format limitation, the image can not be explored or mounted. 

---

