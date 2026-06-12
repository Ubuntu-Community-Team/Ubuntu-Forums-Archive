---
title: "File corruption"
date: 2007-02-14
forum: General Help
---

### Post by jazzgossen on 2007-02-14
For some time now, I've noticed that more than a few files on my system have been damaged. Most notably image and music files. I've seen the following symptoms:

[LIST]
[*]The damaged JPEG files have got a sort of "offset" someway down the image, and when opening them in the GIMP, I get the message "Corrupt JPEG data: 67 extraneous bytes before marker 0xd9". I've attached a cropped version of one of the damaged images here.
[*]The damaged MP3 files play fine in Rhythmbox until somewhere nere the end, where they are cut off, and then they show up as files with errors in the library.
[*]I recently tried to open an XCF image file, but the GIMP said the file was corrupt and unsalvagable.

[/LIST]

I run Ubuntu 6.10 (kernel 2.6.15-26-k7) with ext3 on the devices where the images are, and FAT32 on the device where the music is. I thought that ext3 would be safe, with journalling and all. What's the best way to avoid these problems? Running fsck at every boot? Using another file system? Frequent backups (and in that case, how can I avoid that a good copy of a file gets overwritten by a corrupt version)?

[IMG]http://eyra.se/temp/00101.jpg[/IMG]

---

### Post by lamego on 2007-02-14
Make sure you check your memory with some utility like memcheck, it is very unlikely that you get filesystem corrutption both on ext3 and fat32 unless you have serious hardware problem, mem or hd driver related.

---

### Post by jazzgossen on 2007-02-16
I just ran memtest (from the grub boot menu), and it passed through all the tests once with no errors. 

If there are no other plausible explanations, let's hope that it was my old memory that was faulty. I upgraded the memory a few months ago, and I can't say if the corruptions occurred before or after that.

---

### Post by mrtorrent on 2007-03-10
Hello, I am having a similar problem and I really hope I can find some help.

I backup data from my laptop to a ReiserFS partition on an external hard drive using rsync. I recently decided to switch from Mandriva to Kubuntu, so I ran rsync, wiped the laptop, and installed it. After copying my files back to the laptop I discovered that something like 30% of them were corrupt. All file sizes are correct, but somehow a portion of each corrupt file is missing or garbled or something.

I have also discovered that when I copy files from an SD card using my laptop's built-in flash media reader, I sometimes experience JPEGs that exhibit similar corruption and it takes either remounting the card or sometimes using an external USB reader to copy the file correctly.

I have no idea whether these two problems are related. The symptoms look the same, that's all -- seemingly random file corruption.

Does anyone have any ideas? Is there any way I can try and fix some of these files? I'm particularly concerned about my JPEG photos.

---

