---
title: "Compressing Hard disk"
date: 2008-01-09
forum: General Help
---

### Post by bluesrocker on 2008-01-09
Is there any way I could compress the hard disk to save disk space? Please advice. Thank you:guitar:

---

### Post by SeanTater on 2008-01-09
Technically, it is most likely possible, but it's ridiculous in most cases. You should never need to compress your whole hard drive.

However, if you have specific files you need to compress ( which are not system files like in /etc, /usr and the like) then you can archive them using archivers like file-roller and ark. 

Note that images, videos, music, ISO's, executables and the like will not compress well. Archival is generally intended for text files.

---

### Post by 50words on 2008-01-09
If you compressed everything, your system would slow to a crawl. You are better off getting an external hard drive to hold all those big music and movie files.

---

### Post by bluesrocker on 2008-01-12
Thanks guys.:guitar:

---

### Post by amo-ej1 on 2008-01-12
There are some things you should keep into mind. Typically you're thinking about compressing large files (iso's avi's mp3's ) and such to save space. But you should keep in mind that binary files don't compress that well. So the gain of compressing a large avi will be nothing when compared to compressing the kernel source code (which is ascii with lot of repetitive parts). This just as an example.

Then you should also keep in mind that when working with a compressed filesystem, this will (think about using a live cd) either eat up RAM to store the decompressed data and make everything tremendously slow. 

So the best approach is, as pointed out here, buy some cheap external haddrive (those don't cost any money anymore nowadays) or simply use gzip, zip, or rar to compress a set of files you don't use that often.

---

