---
title: "Extensive copying and backup issues."
date: 2018-10-04
forum: General Help
---

### Post by Lloyd_Hayes on 2018-10-04
I seem to be running into problems with backups and simply copying of large files to USB hard drives. Up to 35 GB in size files. 
This is an old issue that I have dealt with before, and it has always been a permissions issue. But this time that does not seem to be the case. I can copy smaller files, but errors are reported when larger files are being transferred.

Attaching log txt file, which was rated as "Important" by the log reader.

---

### Post by speartip on 2018-10-04
You'll need to give more information, like what version & flavour of Ubuntu you are using? How are you trying to copy the files? What Backup program are you using? etc....
edit.. I see it's Ubuntu Studio, what version?

---

### Post by ajgreeny on 2018-10-04
We also need to know what filesystem the USB has been formatted to; there is a 4GB filesize maximum for fat32, but a great deal larger for most other filesystems.

See [https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits) for all the details.

---

### Post by TheFu on 2018-10-04
Pro tip - use a backup tool for doing backups.
Another pro-top, avoid using GVFS connected storage.  It is very slow.  If you use a real mount, one that will actually show up in the mtab, that would be helpful for speed. Might want to use something non-GUI for this.

No clue about issues from the description or logs. The logs aren't very useful. Anything in dmesg about the hardware?

---

