---
title: "app to make disk image and explore the files"
date: 2007-10-26
forum: General Help
---

### Post by paridoth on 2007-10-26
i am about to backup a clients windows 98 computer and install xp for them, i plan to insert his hard drives into my Ubuntu machine and use partimage to make an image of his fat32 drives so that i can restore them if the xp install doesn't work out. 
however if the xp install does work out i want to be able to pick certain files from the images that he wants to put on his xp install, which is not currently possible with part image.
 i was wondering if there is a linux app i could use to do this. i was also thinking about using part image to image the drive, and then just using "tar" to compress the files in the drive into a gzip file, and them pulling the files he needs from it. although this seems wasteful as it uses twice the space and twice the time. thanks for any help

---

### Post by ddrichardson on 2007-10-27
You should be able to create an image with dd```
dd if=/dev/hda1 of=/home/hda1.bin
```Then mount it as a loopback device:```
sudo mount hda1.bin /media/wherever/ -t ntfs -o loop
```Don't know if it'll work but its worth a try. If it does work it'll let you do what you're asking.

---

