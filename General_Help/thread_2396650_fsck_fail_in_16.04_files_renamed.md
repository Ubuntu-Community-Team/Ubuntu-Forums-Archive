---
title: "fsck fail in 16.04 files renamed"
date: 2018-07-18
forum: General Help
---

### Post by Gnusboy on 2018-07-18
I had a boot fail in 16.04 with the unexpected inconsistency to file system  /dev/sda9 the boot partition. It called for the manual fsck and went to the initramfs prompt. I used a live CD to start the fsck process. The fix said to hit yes all the way through the process.

As I did this, it started renaming all the files. It was showing gnome-documents_gnome-books.png' in lost and found #395353 (395353) has non-unique filename rename to gnome-documents_gnome-books.pn~O <y> ? yes

As the process continued I kept hitting yes at each line. After many, many (75 or 100?) lines of this I stopped the process.

I don't know what effect this has on my system. I have not rebooted it out of caution, because I don't know if it can be undone, or if it is something normal. I have not found that answer. I checked AskUbuntu and couldn't find what I need.

Can anyone explain what is happening and what I should do? I appreciate any help with this. Thank you.

---

### Post by Gnusboy on 2018-07-19
I guess I'm a pariah. Never had 2 posts totally ignored before

---

### Post by TheFu on 2018-07-19
Before attempting any data recovery efforts, creation of a bit-for-bit backup is required. You should do that first.

Lots of files lost is never good.  IME, issues like this usually trace back to a failing disk, so if you don't have a good backup, you should ASAP.  After that, you can check the SMART data.  Hopefully, it will clearly show the issues, but it might not show anything wrong. over 20% of disk failures don't show any issues in the SMART data. Use smartctl to see the data, but make that image/backup first.

If it isn't a failing disk and the partition is ext3/4 or some other highly trusted file system, then it is probably a bad  cable or failing controller port that caused the file corruption, assuming the machine hasn't been repeatedly powered off or hard-reset a few times.

---

### Post by Gnusboy on 2018-07-20
Thank you. I really appreciate youir help

---

