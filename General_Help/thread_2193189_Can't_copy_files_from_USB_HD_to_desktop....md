---
title: "Can't copy files from USB HD to desktop...?"
date: 2013-12-11
forum: General Help
---

### Post by dorigoluca on 2013-12-11
Hi, I recently switched from a mac to my new ubuntu laptop and I copied most of the important files I had on my old computer to an external Hard Disk.

Now I am trying to copy these to Ubunto but when I do, it works well with some files bit for others it tels me:

[IMG]http://img36.imageshack.us/img36/3271/hvb7.png[/IMG]

I tried to use ''sudo chmod -R -v 777 *'' on both the hard disk and my home folder but it didn't change anything ;[

Am I doing something wrong? ty!!!

---

### Post by ajgreeny on 2013-12-11
How is the external drive formatted?

Can you try copying that troublesome file to somewhere else to see if its the source file or the destination partition/folder that is causing the problem; if it will, for example, copy to another external flash drive (FAT32), then we know that it is not a problem of the file itself, unless it's a permissions problem related to it going to a Linux filesystem formatted disk when you try to copy it to your /home/luca/Desktop.  However, if the external drive you have is formatted as FAT32 as many are, the files on it will not have any permissions as far as Linux is concerned.

---

### Post by dorigoluca on 2013-12-11
The format of the drive is hfs+.

I managed to copy all files to a folder (I should be saying directory now :-p ) on my desktop by typing '' sudo cp -r /media/luca/Empty/* HDD '' in th terminal, but now they seem to be locked to that folder... some of the files I can move just fine but other have a little ''lock'' on their icon and I don't really know what to do with that... :)

thank you for your answer!

---

### Post by dorigoluca on 2013-12-11
Ok, i did sudo chown -R luca /home/luca/Desktop/HDD and it work fine. Thanks anyway :))

---

