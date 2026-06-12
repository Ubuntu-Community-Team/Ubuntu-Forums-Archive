---
title: "dd produces different images of same sd card depending on used card reader"
date: 2018-08-09
forum: General Help
---

### Post by d.hostettler on 2018-08-09
Hello everybody!

I installed ubuntu server 18.04 an SD card using this device: [https://www.pcengines.ch/apu2c4.htm](https://www.pcengines.ch/apu2c4.htm). The device can boot from the SD card, everything is working fine. fdisk shows the following info about the SD card:

&#10140; sudo fdisk -l /dev/sdb
Disk /dev/sdb: 14.6 GiB, 15640035328 bytes, 30546944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0809ab2e

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 6836223 6834176  3.3G 83 Linux

The SD card is 16GB but i choose to made the partition only 3.5GB big. The rest of the disk is not used at the moment. The filesystem of the partition is ext4 and I use grub2 as a bootloader.

Now I wanted to use dd to create an image of the SD card and later copy that image to other SD cards. I've done that many times before and it never was a problem.

I try to copy only the partition and all the stuff before it which should be the MBR, partition table and the boot loader. So i came up with the following command:

sudo dd if=/dev/sdb of=my-image.img bs=512 count=6836224 status=progress

count=6836224 is the same number of sectors as the last sector of the partition + 1 because sectors start to count at 0. I think it should work like this, but would be nice if somebody could confirm that.


Now to my problem...

Depending on which PC and which SD card reader I use I get different images from the same SD card. The card is write protected with its little switch on the side of the card, so I'm sure the data on the card stays the same. I use md5sum to check if all the produced images are the same or not. Some of the images are broken and can't be mounted, others seam to work fine, some seam to work mostly ok but only a few files are corrupt (content of one file ends up in another file). I'm quite sure that there are no corrupt files on the original SD card.

If I use the internal card reader of my PCs the card is shown as /dev/mmcblk0. When using an external card reader connected with USB, the card is shown as /dev/sdb or /dev/sdc etc.

Here is a list of my results:

PC 1, internal card reader, /dev/mmcblk0,    4e7a3cc0392389df9a100ea6602d3b87    mount ok, files seam ok
PC 1, external card reader, /dev/sdb,         7775c6f2d4ff11afec14529c30caf5ea    mount fails

PC 2, internal card reader, /dev/mmcblk0,    afcaa607...                                                mount ok, files seam ok
PC 2, external card reader, /dev/sdc,         7775c6f2d4ff11afec14529c30caf5ea    mount fails

PC 3, internal card reader, /dev/mmcblk0,    afcaa607...
PC 3, external card reader, /dev/sdc,            7775c6f2d4ff11afec14529c30caf5ea

To get the md5sums I first created the image with the dd command shown above and then used "md5sum my-image.img" or directly calculated the md5 hash without writing the image like this:

sudo dd if=/dev/<device> bs=512 count=6836224 status=progress | md5sum

Some info about the 3 computers might also be interesting:

PC 1:
dd (coreutils) 8.25
uname -a: Linux pc1 4.15.0-30-generic #32~16.04.1-Ubuntu SMP Thu Jul 26 20:25:39 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

PC 2: 
dd (coreutils) 8.25
uname -a: Linux pc2 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

PC 3:
dd (coreutils) 8.13
uname -a: Linux pc3 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 17:31:43 UTC 2013 i686 i686 i386 GNU/Linux


Can anybody explain, why these images are not the same all the time and what I could do to get an image which is guaranteed to work and have no corrupt files?

Any help or advice would be really appreciated!

Daniel

---

### Post by sudodus on 2018-08-09
It seems that

- the internal card readers do a good job,

- the external card reader (USB adapter) does a bad job, but it produces the same result in all three computers (as shown by the md5sum).

0. Please unmount the partition on the SD card before cloning with dd.

1. Please run the following commands to flush the buffers and make sure that you are 'looking at' the correct data after cloning with dd and before checking md5sum and/or unplugging the SD card,
```

sync
sudo partprobe

```

2. Please check, if the image file will have the same size when cloned from the internal card reader and from the external card reader.

If another size, it is obvious why things go wrong.

Otherwise there is another problem, maybe there is a buffering problem in the external card reader, or maybe the linux driver that is selected for the task does not work well with it.

---

### Post by HermanAB on 2018-08-09
My guess is that the card is mounted automatically, which then messes up the copying.  

You got to plug it in, check that it is OK with 'dmesg', 'umount' it and then only use 'dd' or 'cat' to copy it.

Finally, after copying, run 'sync', to flush the buffers before you remove it.

---

### Post by d.hostettler on 2018-08-09
Hey guys, thanks alot for your advices!

When I insert the card it is mounted automatically but I always unmounted it before executing dd. At least the sizes of the 2 images from PC 1 are the same. I couldn't check the sizes of the other images yet. As far as I understand "sync" and "partprobe" shouldn't be necessary if I directly calculate the md5 sum without writing anything to any disk using the following command:
 [COLOR=#000000]sudo dd if=/dev/<device> bs=512 count=6836224 status=progress | md5sum

[/COLOR]Meanwhile I tested the same process with 2 other SD cards. Card 1 is 8GB with one 8GB partition with an ext2 filesystem and card 2 is the same type as the original card with more or less (but not exactly) the same content as the original. With both of these cards I had no problem at all, all the images produced with different PCs and card readers had the same md5 sum. To me this looks like there are 2 explanations:

1. There is a Hardware-Problem with the original card or
2. The Problem is caused by the content/data of the original card

Although I think #2 is quite unlikely because dd shouldn't care about what data it is copying. So my next step will be to make a fresh ubuntu installation on a new 16GB SD card (the same type/model as the original card) and do all the tests again with this new card.

I'll let you know how it turns out...

---

### Post by sudodus on 2018-08-09
There could be a compatibility problem between the external card reader (USB adapter) and the SD card, that is not cloned correctly.

I agree, that "The Problem is caused by the content/data of the original card" is quite unlikely because dd shouldn't care about what data it is copying.

---

### Post by d.hostettler on 2018-08-09
Ok here's my update...

Making a fresh ubuntu installation an a new SD card produced the same problems when later creating images of this card:

```

PC 1, external card reader, f34425a1f7e49f172c152fe478277ff0

PC 2, external card reader, f34425a1f... (even tried twice, same command, same hash)
PC 2, internal card reader, d055fd83e... (even tried twice, same command, same hash)

PC 3, internal card reader, d055fd83e...
```

Also I got the same kind of results with a 3rd SD card with also a fresh ubuntu installation on it but with an ext2 filesystem instead of ext4.

So the SD card itself shouldn't be the source of the problem.

All the ubuntu installations (ubuntu server 18.04) mentioned above and in the previous posts i did by inserting the SD card in the internal SD card slot of my APU2c4 device, booting the ubuntu installer from a USB stick and follwing the installation instructions, and installing to the SD card in the internal SD card slot. The SD card is shown as /dev/mmcblk0 in the installer.

Then I did another fresh installation, but this time with the SD card in an external USB reader instead of the internal slot. Now the SD card is shown as /dev/sda in the installer. After the installation I booted from the SD card still in the external reader, boot works fine. Then i shutdown and did the same tests with dd | md5sum again. And all of them produced the same md5sum, exactly as it should be!

Then I put the SD card in the internal slot of the device, could successfully boot, shutdown and did the tests again. Still everything ok, all the same hashes. So it looks like it depends which SD card reader is used during the installation. With the internal one I get the problems, with the external one it seams to work just fine (until now at least). This just all seams quite strange to me. Anybody has an explanation for this behaviour?

I will now continue to work with the SD card from the last test, finish to configure everything I need and later try again to make an image of it and do the tests with the md5 sums.

---

### Post by sudodus on 2018-08-09
This is confusing!

Am I reading correctly, that this time the *external* card reader it seems to work just fine, but earlier (reported in the first post), the internal card reader worked just fine. Or did I misunderstand? In that case, what did I misunderstand?

---

### Post by d.hostettler on 2018-08-09
In the first post it was about the problem when generating an image of the SD card by reading from the card. This didn't work with the external card reader (tested with 2 different readers by the way). With the internal readers of 2 different PCs I got images with the same md5 sum and i was able to mount these images and access the files. Although I'm not sure if there are no corrupt files an these images. I had images with some files being corrupt but I'm not totally sure which images these were, sorry! I ended up with so many cards and images, it's hard to not getting confused.

In the last post it was more about how I setup the SD card(s) at the beginning before I create an image of the finished card. So here it's about writing to the card, before it was about reading from the card. And it's true that when I install ubuntu on a fresh card using the internal SD card slot of the APU2c4 device (this one: [https://www.pcengines.ch/apu2c4.htm](https://www.pcengines.ch/apu2c4.htm)) I end up with the problems described in the first post when creating an image of the card. And if I install ubuntu on a fresh card using an external SD card reader connected to the APU2c4 via USB there are no problems when I later create an image of this card.

Hope this makes it a bit more clear. ;)

---

### Post by sudodus on 2018-08-09
Yes, it does. Thanks :-)

But I must admit that I cannot understand why you have such problems.

Have you tested USB 3 ports and also USB 2 ports, if both are available on one of the computers? A USB 2 port (with its lower speed) might work in a more reliable way.

[hr][/hr]
You could also download a Clonezilla iso file (I use and would recommend a *stable* version), create a Clonezilla live drive, and try to clone from the SD card to another SD card or USB pendrive and/or create a Clonezilla image (which is a directory with a number of files, where the big ones are compressed). It might or might not work in a more reliable way.

Clonezilla is safer than dd, because there are checkpoint questions. Clonezilla is also faster, because it is smart enough to only copy used blocks (and skip free space in the file system(s)).

See this link, [https://clonezilla.org](https://clonezilla.org)

---

### Post by d.hostettler on 2018-08-13
The SD card I had in the external card reader when install ubuntu on it is still working fine and doesn't make any problems when creating an image of it.

I didn't use clonezilla yet but if I have some problems again I will give it a try.

On my laptop I have only USB 3 ports but there are also some USB ports on it's docking station. These are listed with a speed of 480M when I type "lsusb -t". So they are USB 2 I guess. But it doesn't make any difference which USB port I use, when creating an image.

And thanks again for your help!

---

