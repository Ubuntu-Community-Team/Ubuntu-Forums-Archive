---
title: "Moving an 80 gig file - into external drive - failure at 4 gig every time"
date: 2022-11-18
forum: General Help
---

### Post by DVD-R on 2022-11-18
Hello,
I have a working 235 gig hard drive which had windows 10 in it 
I pulled it out of a laptop.

I used wipefs -a to wipe the disk clean
And then used cfdisk to create a partition for the full 235 gig.
Then used Ubuntu's DISK application to format the partition as FAT32.

So far so good!
Ubuntu recognizes it when I plug it into a USB cradle - and indicates it is a 235 Gig FAT32 drive.

Here is the weird thing:
I have an 80 gig virtualbox image I was hoping to load onto this disk.
But every time I get a little over 4 gig onto the disk - I get a "Disk Full" error.

This happens both in Ubuntu and in Windows 7
They both see the drive as 235 gig of space.
And they both choke trying to load the file onto it - when the copied file size is around 4 gig

Your wisdom and suggestions greatly appreciated!
Sincere Thanks!

---

### Post by Tadaen_Sylvermane on 2022-11-19
Fat32 caps at 4gb file size... reformat to ext4 or ntfs if the drive needs to be windows capable.

---

### Post by HermanAB on 2022-11-19
Alternatively, if you Have to use the sad Fat32, then you need to split (dd) and merge (cat) the file into smaller chunks.

---

### Post by DVD-R on 2022-11-19
Wonderful!
Thank you all very much!
I never knew about the 4-gig maximum for any given file within FAT32
Greatly appreciate!

---

