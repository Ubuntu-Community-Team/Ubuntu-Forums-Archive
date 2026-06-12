---
title: "BTRFS compression"
date: 2020-01-13
forum: General Help
---

### Post by chris-hancox on 2020-01-13
Hello,

My laptop has a 64GB eMMC drive with no room for upgrading. I am using BTRFS on Ubuntu 19.10 so I can compress the disk.

So far, I have noticed that you have to manually do ```
sudo btrfs filesystem defragment -c / -r 
``` to compress the disk. This means that as files change I have to re-run this command to compress files and save space. In addition, I have noticed that in some cases files can become larger! Is there a way to have the compression run automatically, and also only take effect on files which will benefit from compression?

---

### Post by HermanAB on 2020-01-13
I would get a large Class 10 SD card, plug it in and use it as the main HDD.

---

### Post by chris-hancox on 2020-01-14
Unfortunately not possible as the SD card reader does not work and at the moment I have no money for a new machine.

---

### Post by Impavidus on 2020-01-15
I've never used btrfs, but I doubt you'll gain much from compression on filesystem level.

Plain text files are highly compressible, often to around 15% of their original size. However, they are so small that this doesn't matter on any drive larger than 1GB. Media files can fill a 64GB drive, but they are already compressed, so further compression will yield nothing. Then there are some very inefficient file formats, like computer-generated specimens of human-readable files (xml, postscript) or large databases in plain text, but they are better handled by compression on a file level. Overflowing log files should be dealt with by eliminating the source or repeating messages.

My guess is that over 80% of your disk space is taken by files that won't benefit from further compression. Can you move some media files to an external drive?

---

