---
title: "Error correction and or protection ?"
date: 2015-02-18
forum: General Help
---

### Post by birkopf on 2015-02-18
Hi guys,

Very often I have to back up data or simply copy large amounts of data
(>100GB each time). Copying on Linux is a pleasure, but errors do come from
time to time. Especially if I need to copy from ext4 partition to ntfs and so
on. Seems that cluster sizes and different architectures not always are fully
compatible... not mentioning fat32 where you cannot copy filers larger then
4GB. 

Many programs have CRC correction options (like zip and rar archivers). Some
CD/DVD burning programs also have protection for data which are preventing
data loss and data errors. 

Is there any program or support library on liunx that would help monitor
process of copying files and prevent data loss / errors ?

---

### Post by HermanAB on 2015-02-18
You can use rsync as a better copy program.  Read the man page.

There is also rsbep and par2.

[http://www.aeronetworks.ca/search?q=protect](http://www.aeronetworks.ca/search?q=protect)

---

### Post by tgalati4 on 2015-02-18
Instead of using ext4, you could try ZFS which has CRC built-in.  Of course, it may not play well with NTFS either, so that you will have to research.

---

### Post by birkopf on 2015-02-18
Sounds interesting. I will try converting one partition to ZFS and see how it works.

---

