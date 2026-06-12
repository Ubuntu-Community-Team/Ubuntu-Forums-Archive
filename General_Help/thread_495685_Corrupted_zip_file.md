---
title: "Corrupted zip file"
date: 2007-07-08
forum: General Help
---

### Post by The-Sam on 2007-07-08
Before I installed Ubuntu on my HD, I put all of my files (the Documents and Settings folder) into a zip file on another HD (the installer's built in thing wasn't working). I checked it in Windows with WinZip, and it worked fine, but now with the Archive Manager in Ubuntu, it says:

```
Archive:  /media/stuff/2007 Documents and Settings.zip   29273513618   33940
warning [/media/stuff/2007 Documents and Settings.zip]:  24971917323 extra bytes at beginning or within zipfile
  (attempting to process anyway)
error [/media/stuff/2007 Documents and Settings.zip]:  start of central directory not found;
  zipfile corrupt.
  (please check that you have transferred or created the zipfile in the
  appropriate BINARY mode and that you have compiled UnZip properly)
```

The files in the zip are very important - is there any way to extract them from the zip?

---

### Post by negated on 2007-07-08
Are these files being stored on an NTFS formatted partition? If so, try copying it to the native Linux partition (however you have it formatted) and try opening it from there.

I use NTFS-3G and found this is the case many times. For example, if I just download a file (say, for a theme...a tar.gz type file) and save it directly to an NTFS partition via NTFS-3G. When the archive manager tries to open the file, it will say it's corrupted. If I download it to say, my desktop first, then it will work perfectly.

Not sure what the (permanent) solution is, but just wanted to confirm the symptom at least!

-S

---

### Post by The-Sam on 2007-07-08
Yes, they the file is on an NTFS partition, but moving them didn't work, it still has the same error.

---

### Post by szaka on 2007-07-08
> **negated said:**
> Are these files being stored on an NTFS formatted partition? If so, try copying it to the native Linux partition (however you have it formatted) and try opening it from there.

I use NTFS-3G and found this is the case many times. For example, if I just download a file (say, for a theme...a tar.gz type file) and save it directly to an NTFS partition via NTFS-3G. When the archive manager tries to open the file, it will say it's corrupted. If I download it to say, my desktop first, then it will work perfectly.

Very strange. Nobody ever reported such problem to NTFS-3G development. Would you please reproduce the problem with a file by downloading it to both NTFS and a Linux partition then send the outputs of the below commands?
```

ls -l ntfs-path/file linux-path/file
md5sum ntfs-path/file linux-path/file
egrep -i 'fuse|dma|ntfs' /var/log/daemon.log

```
Thanks in advance.

---

### Post by negated on 2007-07-08
The test file came from: [http://art4linux.org/?q=node/17](http://art4linux.org/?q=node/17)

ls -l ntfs-path/file linux-path/file shows:

```

ls -l Desktop/waves.tar.gz /media/sda5/Ubuntu\ Stuff/Themes\ \&\ Icons/waves.tar.gz 
-rw-r--r-- 1 sboyle sboyle  508503 2007-07-08 17:09 Desktop/waves.tar.gz
-rwxrwx--- 1 root   plugdev      0 2007-07-08 17:11 /media/sda5/Ubuntu Stuff/Themes & Icons/waves.tar.gz
```

md5sum ntfs-path/file linux-path/file shows:

```
md5sum Desktop/waves.tar.gz /media/sda5/Ubuntu\ Stuff/Themes\ \&\ Icons/waves.tar.gz 
33629360271b13691da3d9ddc05d8f94  Desktop/waves.tar.gz
d41d8cd98f00b204e9800998ecf8427e  /media/sda5/Ubuntu Stuff/Themes & Icons/waves.tar.gz
```

egrep -i 'fuse|dma|ntfs' /var/log/daemon.log shows:

**Nothing!**

FYI, it is the latest version from the Feisty Universe repository, 1:1.328.1. I'm running Feisty 32-bit. I haven't messed with Nautilus or NTFS-3G (other than installing it). I realize now that it is writing 0 byte files. I have no idea why. If I download the same file to my ext3 partition first and then copy/move it over, it works fine from there on out.

Please let me know if there is anything else I can do...

-S

---

### Post by szaka on 2007-07-08
> **negated said:**
> 
FYI, it is the latest version from the Feisty Universe repository, 1:1.328.1. I'm running Feisty 32-bit. I haven't messed with Nautilus or NTFS-3G (other than installing it). I realize now that it is writing 0 byte files. I have no idea why. If I download the same file to my ext3 partition first and then copy/move it over, it works fine from there on out.

Excellent, thanks! This is a known Firefox bug with NTFS and FAT partitions:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65164](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65164)
Hopefully there is or will be soon a fixed Firefox package for Feisty.

---

### Post by negated on 2007-07-08
> **szaka said:**
> Excellent, thanks! This is a known Firefox bug with NTFS and FAT partitions:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65164](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/65164)
Hopefully there is or will be soon a fixed Firefox package for Feisty.

Awesome! Thanks for the info...

Sorry for the wild goose chase!

NTFS-3G rules! Keep up the good work.

-S

---

