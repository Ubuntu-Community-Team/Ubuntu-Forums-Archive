---
title: "FAT16 not mounting"
date: 2008-04-21
forum: General Help
---

### Post by cometa2k7 on 2008-04-21
I have an 8Gb Memory Stick Pro Duo, for my mobile phone.

I bought it without realising that my mobile only supported FAt16, so 2Gb is the limit on size.

However, when I put it in, it worked fine for a month or so, but when I went over about 4Gb of music files, it stopped working.

I recently managed to rescue it, as it hadn't been working, and I manageed to format it as a 4Gb partition, in FAT16 format. GPArted allowed me to do this, and said that 4Gb was the limit for FAT16.

The only problem is that even though my computer can see that the memory stick exists, it is unable to mount it, and it says:

[SIZE="3"]**"The volume uses the  file system which is not supported by your system."**[/SIZE]

My computer seems unable to mount it. But it mounts my mobile phone perfectly, and that is FAT16.

---

### Post by matey3 on 2008-04-22
I had the same problem with an actual hard drive. I unmounted it,ran the fdisk and mounted it again , it recognized it and I am using it right now? I am not really sure what I did? but I was getting the same message about it being wrong file system etc. but now it works fine?!

---

### Post by cometa2k7 on 2008-04-25
I gave it an entry in /etc/fstab, and formatted it to 4Gb, and it seems to work.

I'm just wasting the other 4Gb, but at least I got it past the 2Gb limit.:lolflag:

---

