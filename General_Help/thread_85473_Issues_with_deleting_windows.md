---
title: "Issues with deleting windows"
date: 2005-11-02
forum: General Help
---

### Post by augied on 2005-11-02
I'm fairly new to linux. I wouldn't call myself a beginner, but I'm definitely lacking certain skills.  I recently reformated my windows partition, deleting windows for good.  I now want to put my Ubuntu installation on the primary partition.  Two questions; first, how do I do this, and second, how do I move grub onto the master boot record?
Thanks

---

### Post by mykey on 2005-11-02
.. deleting it for good, hm ?! brave move - just go for it - put in the cd and start the install - it will ask you where you want to put the system and at the end it will ask you where you want to install the bootloader ..

---

### Post by aysiu on 2005-11-02
At a certain point in the installation you'll be asked whether you want to erase the entire disk or manually edit the partition table. It sounds as if you want to erase the entire disk.

---

### Post by augied on 2005-11-02
Sorry, I guess I wasn't clear enough.  I already have Ubuntu installed on an extended partition.  I need to move that existing installation onto the primary partition.

---

### Post by metwo on 2005-11-02
Assuming you have already deleted all the data off the primary partition, and assuming it is /dev/hda1, you first need to change the partition type in fdisk to 'linux'.

Do this with 

```
sudo fdisk /dev/hda
```

then hit t to 'change a partition's system id', you need to select partition 1 (assuming thats the one you want to change) and change it to type 83 (linux). Then hit 'w' to save changes and exit. Be careful with fdisk though, as you can really mess stuff up. If you're not sure of something when using it, hit ctrl-c to exit and ask someone!

Then you need to format the primary partition in a linux-friendly format, such as ext2 or reiserfs. Ubuntu uses ext3 by default I think, so that would be a good choice. Do this with

```
sudo mke2fs -j /dev/hda1
```

Its probably best to then reboot to a live cd (e.g. knoppix), mount /dev/hda1 and /dev/hda2 (assuming hda2 holds your current ubuntu directory) to /mnt/hda1 and /mnt/hda2, then do a

```
cp -a /mnt/hda2/ mnt/hda1
```

having done this, you need to edit /mnt/hda1/etc/fstab and change /dev/hda2 to /dev/hda1. Also, change the root=/dev/hda2 line to hda1 in the file /mnt/hda1/boot/grub/menu.lst (there may be some other mentions of hda1 you need to change as well)

Then, you'll need to reboot to ubuntu and do a

```
sudo grub
```

Once in the grub console, you'll need to do

```
root(hd0,0)
setup(hd0)
quit
```

---

### Post by augied on 2005-11-02
Thanks, great instructions.  I'll do that.

---

