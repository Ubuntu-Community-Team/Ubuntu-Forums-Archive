---
title: "how to make a larger casper.rw file on bootable USB"
date: 2016-07-05
forum: General Help
---

### Post by Evil Wayz on 2016-07-05
Due to a massive lightning storm All my pc are down waiting on new power supplies.  In the meantime, I am using a laptop with no hard drive in it and booting xubuntu from a usb key that was created with unetbootin.

The computer crashes or freezes up a lot, so I decided to use the persistence feature, but the largest space available is 512mb.  Does anyone know how to make a larger casper.rw file, at least 1024mb?

ATTENTION ADMINS: Can someone please change the thread title?  Not sure what happened there but its from a different post.

---

### Post by yancek on 2016-07-05
You should be able to make a persistence "file" of up to 4GB.  That limitation is because of FAT32.  If that does'n't work, follow the instructions at the link below to create a separate persistent "partition".

 [http://askubuntu.com/questions/138356/how-do-i-get-a-live-usb-to-use-a-partition-for-persistence](http://askubuntu.com/questions/138356/how-do-i-get-a-live-usb-to-use-a-partition-for-persistence)

---

### Post by Evil Wayz on 2016-07-06
Ok I followed the instruction in both of the ways presented, and while the usb key boots up successfully, it is not writing to the large casper-rw partition.  Also when i checked the booting command in grub, i had to add " persistent" because it wasn't already there.  But when i check my syslinux.cfg file, the persistent command is where it is supposed to be.  

Maybe I don't understand this correctly, but I thought that what ever i downloaded or any programs i installed would be saved directly into the second partition, named casper-rw.  But it doesn't, and I can't write to it directly either.

---

### Post by yancek on 2016-07-06
Give an example of a program you downloaded and how as well as where you downloaded it from.  I don't use this much but have created persistent systems and installed software which was available on reboot.  How do you try to access software you have downloaded, an example please.

The casper-rw partition is outside the /home/user directory which means like most everything else located outside of it, you need to either use root permissions (sudo) or change the owner:group of the partition directory mount point.

---

### Post by Evil Wayz on 2016-07-06
I am downloading programs from the repositories, and doing system updates.  And everytime i have to reboot, which is a couple times a day until I can get a hard drive for this pc, i have to set the time and the volume and change some settings on the touchpad and download gimp and putty and then sign into sync on firefox again.  

I assume when i download smplayer, for example, it's downloading it into ram. and when i call for it, it runs out of ram.

I also assume when i download an image off the internet and save it in pictures that is also in the ram.  I would like for anything i do while running off the key, to be permanent.  

What I'm looking for basically is a usb key that makes any computer i come across into my personal computer.  I thought that is what that how-to was supposed to accomplish.

---

### Post by sudodus on 2016-07-06
If you want a persistent live system that works with all current Ubuntu desktop flavours (standard Ubuntu, Kubuntu, Lubuntu ... Xubuntu), you can make it automatically with mkusb, if you intend to install the whole system including the casper-rw partition into the same drive (USB pendrive, external HDD, SSD).

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

If you intend to install the casper-rw partition into another drive (not the drive you boot from), I suggest that you do it manually. The Ubuntu engine under the hood will recognize a file with the name casper-rw, or a partition with the label casper-rw, but you should have only one such file or partition, so remove the file if you want to use a partition for persistence.

---

### Post by Evil Wayz on 2016-07-06
The drive i have right now has the os on a fat32 partition.  It is followed by an ext2 partition named casper-rw.  I deleted the casper.rw file in the first partition.  But Ubuntu isn't recognizing the partition or using it.  I missed a step somewhere.

---

### Post by sudodus on 2016-07-07
Ubuntu wants the boot option **persistent** (not persistence or something else, check for typing errors) to invoke the persistence.

If you still have problems, I suggest that you try with ***mkusb*** (to overwrite your current system.

If you have an HP computer, you should select an MSDOS partition table, otherwise I would recommend the GUID partition table (GPT). You will be prompted in a separate window to make this decision.

---

### Post by Evil Wayz on 2016-07-07
I have tried adding persistent after "quiet nosplash" when the system boots.  I have tried adding persistent after the same commands in syslinux.cfg.

I don't understand most of that mkusb guide so I guess I'll just deal with this til i get a new hard drive.

---

### Post by sudodus on 2016-07-08
I hope and think you will soon find the final clue to make persistence work. For example, you can search for posts by *C.S.Cameron* at our Ubuntu Forums.

Good luck :-)

-o-

Finally, please come back if you want to try along another route.

---

### Post by C.S.Cameron on 2016-07-09
Persistent partitions are not working with 64 bit versions of Ubuntu post 12.04 made with UNetbootin or USB Creator.
I recall 32 bit 16.04 worked for me with casper-rw and home-rw partitions.
I have had good luck using mkusb to make a drive with persistent partitions.
A grub2 iso install also works with persistent partitions, (see MultiBootUSB).
You can mount your old casper.rw or home-rw file and rsync the data to a new casper-rw file or partition.
You can also do a full install to USB similar to installing to internal drive but the drive needs to be larger than 4GB.

---

### Post by Evil Wayz on 2016-07-09
> **c.s.cameron said:**
> 
you can also do a full install to usb similar to installing to internal drive but the drive needs to be larger than 4gb.

boom.

---

