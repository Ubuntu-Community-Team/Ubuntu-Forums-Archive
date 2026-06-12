---
title: "Boot several ISO's from harddrive"
date: 2008-06-22
forum: General Help
---

### Post by Nerden on 2008-06-22
I am trying to make a little project for a small computer repair shop I work for, we currently have about 20 different CD's we use for doing such work,(datarecovery, diagnostincs etc.)

I want to store these ISO's on the harddrive and have them listed in grub or something so I can just select the drive from a list, which would be nice. 

So far all I found was a little tutorial which said i need to format a partition for the iso standard, I have the partitions ready and cannot for the life of me work out how to format said partition.

Thank you for any help

---

### Post by Vivaldi Gloria on 2008-06-22
I don't know the answer to your question but I think you are misunderstanding the tutorial you are following. If you look at

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

then you'll see that

> The currently supported filesystem types are BSD FFS, DOS FAT16 and FAT32, Minix fs, Linux ext2fs, ReiserFS, JFS, XFS, and VSTa fs.

So even if you manage to format a partition in ISO 9660 (and I doubt that you can) you cannot make grub start it. Probably what is meant in your tutorial is to copy the contents of the cd to a new partition.

Googling I found the following link which tells (see post 6) how to start linux live cds by copying the contents of iso to a partition and adding the boot directory to the partition.

[http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/](http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/)

I hope it helps. 

Which tutorial are you following btw?

---

### Post by Nerden on 2008-06-22
[http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/](http://www.linuxquestions.org/questions/linux-general-1/boot-iso-image-from-hard-disk-294744/)

---

### Post by mc4man on 2008-06-22
I'm not to sure what your describing would be possible (formatting a partition to iso9660.) It would seem quite possible to format it/them as normal (fat32, ext2) and have grub read/boot from the image you have inserted. Or while I believe it's used for Os images maybe the loopback comm. for grub could be adapted for your use.
I also remember seeing something called grub4dos  ...?

---

### Post by Vivaldi Gloria on 2008-06-22
> -create a mountpoint to mount the ISO with loopback:
mkdir /mnt/LiveISO

-mount the image:
mount -t iso9660 -o loop,ro /DOWNLOADS/Knoppix-3.7-en.iso /mnt/LiveISO

-create a directory on the device where you are going to boot from:
mkdir /mnt/hda4/KNOPPIX

-copy the contents of the mounted image to that directory:
cp /mnt/LiveISO/KNOPPIX/* /mnt/hda4/KNOPPIX/

-copy kernel and initrd files to yor boot device:
cp /mnt/LiveISO/boot/* /boot

* Grub:
title KNOPPIX
root (hd0,0)
kernel /linux26 ramdisk_size=100000 fromhd=/dev/hda4
initrd /minirt26.gz
savedefault
boot

In this example a new partition hda4 is used. And hda4 can be anything grub understands, like ext3. Then you copy the files there as explained.

You do NOT format the partition hda4 (or whatever you are using) as iso, you just format it as ext3 (or anything grub understands) and copy the files there.

---

### Post by Nerden on 2008-06-22
right o, another problem arises that not all the disks are live CDs.

---

### Post by Vivaldi Gloria on 2008-06-22
> **Nerden said:**
> right o, another problem arises that not all the disks are live CDs.

How are they used normally?

---

### Post by Nerden on 2008-06-22
we just boot the CD as normal after post before the OS loads. we have a machine dedicated for cloning harddrives. basicaly we want this machine to be able to do that and more, using harddrive caddies,

I suppose I dont even have to use linux (God forbid), just some method of storing the ISO's (or their data) and alowing a menu to select from them

---

### Post by Vivaldi Gloria on 2008-06-22
Sorry Pal, I am out of ideas. Anyone?

---

### Post by mc4man on 2008-06-22
Here's a couple of pages that dance around what you're talking about
[http://www.nabble.com/Boot-an-ISO-on-an-external-internal-HD-partition.-to3012082.html](http://www.nabble.com/Boot-an-ISO-on-an-external-internal-HD-partition.-to3012082.html)
[http://mgerards.net/blog/?p=16](http://mgerards.net/blog/?p=16)
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

---

### Post by Nerden on 2008-06-23
Im think the link to marcos blog is what I want, thank you all for your help
[http://mgerards.net/blog/?p=16]("http://mgerards.net/blog/?p=16")

---

### Post by starcannon on 2008-06-23
I would think the way liveUSB works would likely be a great place to start researching your project:

[http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB)

GL and write a guide if you solve please, I'd for one really like to see how you do it.

---

