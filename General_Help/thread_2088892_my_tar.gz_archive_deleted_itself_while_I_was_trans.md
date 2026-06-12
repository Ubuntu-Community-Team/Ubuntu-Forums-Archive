---
title: "my tar.gz archive deleted itself while I was transferring files into it"
date: 2012-11-27
forum: General Help
---

### Post by subvertc on 2012-11-27
I created a tar.gz archive to archive quite a bit of data (pictures). I had transferred about half the data into the archive, and once that was completed, added the second half of the data. When I did so, the tar.gz "deleted" itself. When I try to use Archive Manager to open it, I get a error message stating the file doesn't exist. 

How do I fix this? I deleted the originals after transferring them into the archive, so I am facing a loss of about 7gigs of pictures. :(

I'm running Ubuntu 11.11

---

### Post by varunendra on 2012-11-28
> **subvertc said:**
> I deleted the originals after transferring them into the archive, so I am facing a loss of about 7gigs of pictures.
Immediately stop 'writing' to the partition on which the pictures and/or the archive resided. If it is the same partition where your 'Home' or root directory is, stop booting it at all ! Install testdisk -
```
sudo apt-get install testdisk
```
Then run PhotoRec (part of testdisk package). Do the installation on a live cd/usb if the files were on 'root' or 'home'.

PhotoRec can easily recover lost files unless they have been overwritten.

Photorec Step-by-Step : [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Once you have your source photos back, which is more important, we may discuss about the error and its cause.

.

---

