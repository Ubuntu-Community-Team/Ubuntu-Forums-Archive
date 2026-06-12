---
title: "Using dd to write to physical partition."
date: 2022-03-24
forum: General Help
---

### Post by soulboogie on 2022-03-24
Need some help figuring out what I need to do to take a HDD image and write it to a physical drive as a partition.

Essentially I'm trying to modify a dual boot HDD. I wanna keep one OS while replacing the other. One operating system is win95, the other is MS-DOS 6.2. I'm trying to replace just the MS-DOS partition.

When using fdisk on the physical drive I get 

"Disk /dev/sdb: 4563 MB,
/dev/sdb4
Disk /dev/sdb4: 436 MB,"

I've written dd like this

"dd if=”DOS HDD image” of=/dev/sdb4"

That does copy the image over but I only have MS-DOS and no longer have win95. What can I do to pull this off? Thank you.

---

### Post by VMC on 2022-03-24
First off, I don't use 'dd' for partitions. Instead I would use Clonezilla or my preference is fsarchiver. With that said, what kind of image or backup did you use?

---

### Post by soulboogie on 2022-03-24
Yes both are backed up. 

The dual boot HDD image that has win95 and dos is a .raw (never messed with that file type before). The other HDD image is a .img file.

---

### Post by VMC on 2022-03-24
On second thought fsarchiver won't work with NTFS. What is your partition setup for using these formats?

---

### Post by soulboogie on 2022-03-24
I'm unsure how they are set up, the image was given to me. It's for a PC98. I was hoping I could use editdisk and swap in the files I needed. But it doesn't support that raw image. Not sure if it's the file format or because it's 4gb.

---

### Post by soulboogie on 2022-03-24
The HDD images don't have a filesystem type lol. Idk how, but I'm getting "empty" when using fdisk, and when using file -Ls it doesn't say anything about the filesystem type. So I guess these are unmountable?

---

### Post by VMC on 2022-03-25
Most likely FAT16 for DOS. Which reminds me. You posted in the wrong forum. I think it should be "other systems". Are you trying to get Linux installed. A bit confused.
Is  this your [computer]("https://en.wikipedia.org/wiki/PC-9800_series")?

---

### Post by soulboogie on 2022-03-25
Linux is installed. I'm using it to create HDD images for projects. Should the topic be moved?

Can I specify with -t FAT16, or is it VFAT or something.

---

### Post by deadflowr on 2022-03-25
> Linux is installed.
Ubuntu?

---

### Post by soulboogie on 2022-03-25
Sorry, yes Ubuntu.

---

