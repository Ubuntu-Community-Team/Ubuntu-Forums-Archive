---
title: "Testdisk lists a bunch of nonsense partitions and one REAL partition. What to do?"
date: 2014-06-06
forum: General Help
---

### Post by 777funk on 2014-06-06
I just had a major catastrophe and lost my backup while rebuilding my dual boot (Ubuntu 12.04 and XP) machine. This drive was a 3TB internal backup drive (only data, no boot, and no OS's). I formatted it NFTS and had to format as a 2TB drive (used Acronis). Anyways, I got all the data I needed then foolishly tried to format the missing remainder of the drive in Windows so it'd also be usable. Anyways, it messed with the partition information when I did this and bye bye drive folder.

I was able to go to **TestDisk **and after doing a "Deeper Search" found the data (saving it as we speak). But now I'd like to make the disk readable again. There's only one real partition (the NFTS partition) and a bunch of nonsense partitions or duplicates of the good one. Being unfamiliar with Testdisk, what would I do in order to restore the one real partition? Here's a screen capture of what I've got (see testdisk_goodpartition.JPG). The one with the arrow is the real partition and the rest show "Can't open filesystem" when I press 'p' to show files.

What would be done to get the real partition to become useable again? I'm guessing based on [this tutorial thread link]("http://html5.litten.com/how-to-fix-external-disk-drive-suddenly-became-raw/"), I'd use the right arrow key until there's a P next to this for "primary partition" on that one and leave NO letter by the others, then hit "Write". But I don't know the program well enough to be confident that I'm right enough to hit "Write". There are other options L=Logical, D=Deleted that I'm not sure about. Edit: reading [more]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"), it looks like maybe L is the correct option... I'm guessing here so any tips would be great! 

thanks!!

---

### Post by grahammechanical on 2014-06-06
This might help. It is from the developers web site.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Regards.

---

### Post by varunendra on 2014-06-06
If you are sure the one highlighted in the screenshot is the partition you want, and it was the ONLY partition on the drive, you need to mark it as 'P' > press 'Enter' > highlight 'Write' > press 'Enter' > 'y' > 'Ok'

If there was only one partition on the drive, it can NOT be a Logical (L) partition. The first partition is always a Primary partition.

**EDIT:** Hope you already read this : [http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical](http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical)

However, if you got your data backed up, I recommend deleting the partition table and simply create a new one using Gparted. I have seen problems between gparted and the partitions recovered by testdisk (gparted seeing the space as 'unused'), which indicates that the partition table created by testdisk is probably not a standard one.

---

### Post by 777funk on 2014-06-06
Varun, it worked and thanks! I have a friend studying in the USA named Varun. Great guy. 

And yes, I did read that from the dev's site. I figured it was 'P' but I didn't want to assume anything since assuming was what got me into trouble with the format! 

Thanks for the help.

---

### Post by varunendra on 2014-06-07
You're most welcome! (especially because you said good words for me :p)

Please mark the thread as [SOLVED] using "Thread Tools" link above the first post.

---

