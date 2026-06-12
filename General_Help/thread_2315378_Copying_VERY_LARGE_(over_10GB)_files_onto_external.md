---
title: "Copying VERY LARGE (over 10GB) files onto external HDD failing"
date: 2016-02-28
forum: General Help
---

### Post by shaun57661 on 2016-02-28
Is there a workaround to this? I have some very large video files in mkv format that I'd like to save on an external hdd in case I need to reinstall my OS, but when I do the procedure to copy/paste or even move, it stalls after about 4-6 Gigs then fails.

I'm wondering if I can even do some kind of workaround for a file over 20 GB large.

Please help.

---

### Post by howefield on 2016-02-28
Which file system do you have on the external drive ?

---

### Post by nerdtron on 2016-02-28
> **shaun57661 said:**
> ...it stalls after about 4-6 Gigs then fails.

4GB? If the external hard drive is formatted as FAT32, that's the file size limit. You can't save any file larger than 4GB on a FAT32 file system. OS either you split the file to smaller sizes or format the drive to another filesystem that supports higher file sizes like NTFS (r/w for both windows and linux too) or EXT4 for Linux.

---

### Post by HermanAB on 2016-02-28
First, format the disk with a real file system such as ext4, hfs or ntfs.  Then, copy the files with rsync, since it uses checksums while copying.

---

