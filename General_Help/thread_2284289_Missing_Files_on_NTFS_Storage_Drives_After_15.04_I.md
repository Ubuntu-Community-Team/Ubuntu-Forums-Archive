---
title: "Missing Files on NTFS Storage Drives After 15.04 Install"
date: 2015-06-28
forum: General Help
---

### Post by Alebin on 2015-06-28
I just wiped out win8.1 and installed ubuntu. I have some internal and some external drives dedicated to storage, all ntfs. I have some media files (videos) on an external drive that gets auto-mounted in ubuntu and a mirror backup of those are on an internal drive that doesn't get automounted. I noticed there are at least 3 of those media files now missing, now that I'm viewing the drive(s) in ubuntu. I haven't written anything to the drives, for fear of damaging the data.

I had win8.1 on an ssd dedicated to it, cleared everything off of it and created new partitions for ubuntu. I didn't touch any of the other drives; win8.1 was completely gone when I repartitioned for installing ubuntu. Any idea what's going on?

---

### Post by matt_symes on 2015-06-28
Hi

Are all the NTFS drives SSDs ? If so what make and model ?

Kind regards

---

### Post by Alebin on 2015-06-28
No, all the ntfs drives are standard HDD. The only SSD was the one that had win8.1 that got repartitioned and reinstalled to ubuntu 15.04.

I tried mounting with windows_names and streams_interface=windows, also tried doing  a find command:
find /path/to/ntfs/mountpoint -type f -iname '*pattern*'
and none of these helped.

[B]Edit:
After remounting every way imaginable, twice, I finally got them to show up some how and I'm making backups now to convert the file system to ext4. Thanks for the help![/B]

---

### Post by ajgreeny on 2015-06-28
Please mark the thread as **SOLVED** from the Thread Tools menu at the top.
Apologies, I see you have done so.

---

