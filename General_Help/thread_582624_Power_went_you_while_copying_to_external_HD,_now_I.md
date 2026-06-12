---
title: "Power went you while copying to external HD, now I get an I/O error (pic)"
date: 2007-10-20
forum: General Help
---

### Post by jamesey on 2007-10-20
I was backing up some music and movies TO my external HD. Suddenly the power went off in my building and my computer and my components all shut off. When I turned my computer back on to resume copying the files, I get the following message every time I try to copy from my internal SATA drive to my external USB drive. The files are fine, but my external HD cannot be written to. 

[IMG]http://jamesdemastus.com/aaaaahhhhh/Screenshot-nautilus.png[/IMG]

How do I fix this?

---

### Post by thelocust on 2007-10-20
I dont think you can sounds like the file got corupt. Is it just that file or can you not tranfer anything?

---

### Post by Page on 2007-10-20
I would start by running fsck.

(be sure to unmount the drive first)

---

### Post by HW_Hack on 2007-10-20
Hope you get your file back

Here in Oregon we're having wind storms - we just had a classic 3 - 5 second power hit. My newly upgraded version of 7.10 reported the hit (as my APC UPS kicked in) and kept on chugging.  Cool thing here is (unlike XP) I never had to tell Linux I had a UPS or load drivers etc. as I had to do in XP ------ the UPS was present during the install and Ubuntu just found it.

Ain't that grand

---

### Post by jamesey on 2007-10-20
> **thelocust said:**
> I dont think you can sounds like the file got corupt. Is it just that file or can you not tranfer anything?



I didn't lose a file. I was just backing it up to an external drive when the power went out. The file is fine. The issue is that I can't send anything to my external hdd now. I get the error as shown above.

How do I fsck my external hdd which is /dev/sdd1  ???

---

### Post by Page on 2007-10-20
run

fsck /dev/sdd1

if the drive is fomatted in fat16, fat32, ext2 or ext3.  Fsck won't work on ntfs drives (to the best of my knowledge)

unmount the drive first, or it could hose the filesystem.

---

### Post by jamesey on 2007-10-20
> **Page said:**
> run

fsck /dev/sdd1

if the drive is fomatted in fat16, fat32, ext2 or ext3.  Fsck won't work on ntfs drives (to the best of my knowledge)

unmount the drive first, or it could hose the filesystem.

I did that, and got this:

> fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdd1

---

