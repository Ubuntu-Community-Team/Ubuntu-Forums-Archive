---
title: "[SOLVED] Swap partition"
date: 2008-03-21
forum: General Help
---

### Post by agaudio on 2008-03-21
I have a few basic questions regarding the swap partition. First of all, I am wondering what the optimal size is.  I currently have about 1 GB  ( have 1 GB of RAM on my machine as well). I have heard that if you intend to use the hibernate power saving functionality (which I am thinking of doing), you may need more? I also run Windows XP in Virtual Box from time to time, and I have alotted this virtual machine 512 MB of RAM when it is in use.

My other question is about partitioning. I currently have the following setup, after a good deal of rearranging after removing Windows XP and making my dual boot system into Ubuntu only.

[ATTACH]63287[/ATTACH]

THus, the swap partition still resides in an extended logical partition rather than a primary partition. Is there any reason to try to move it out to a primary partition? Is it difficult to move the swap partition? I should add that the root file system resides on sda4 and that I have an entirely separate hard drive for my home folders and other files. sda1 is a preinstalled Dell Utility partition.

Thanks for any help and suggestions you might have.

---

### Post by erginemr on 2008-03-21
Please refer to this topic for more info on the issue:
[http://ubuntuforums.org/showthread.php?t=730610&highlight=swap+hibernate](http://ubuntuforums.org/showthread.php?t=730610&highlight=swap+hibernate)

I don't think that having it "extended" will cause any problems. If it turns out necessary for hibernation you can use GParted later on to carve out one more 1 GB from /dev/sda2 and combine it with swap making it 2 GB in the end.

---

