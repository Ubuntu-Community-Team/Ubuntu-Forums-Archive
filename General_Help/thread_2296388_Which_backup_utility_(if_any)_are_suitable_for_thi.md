---
title: "Which backup utility (if any) are suitable for this task?"
date: 2015-09-25
forum: General Help
---

### Post by Wiggly_Woogly on 2015-09-25
I have Ubuntu and Windows 7 on separate partitions. Win7 was installed first, because I was advised this was the easiest way to go.

Now I decided that my Ubuntu partition needs to be bigger - else I'm going to run out of space.

What tools can I use to backup/restore my:
[LIST]
[*]applications (in various locations /usr/lib, /usr/share, etc.)
[*]preferences
[*]programming libraries
[*]hardware drivers
[*]personal files
[/LIST]
which DON'T create a perfect image of the disk? A complete image will be unsuitable because I intend to resize the partitions, and allocate more space to the Ubuntu partition, and less to Win7.

Otherwise, I'll need to spend ages making fresh installs of both and slowly reinstalling all my libraries, apps, preferences, drivers and so forth, from scratch. NOT IDEAL AT ALL!!!!

P.S. I heard GParted will resize my Ubuntu partition but might cause both Win7 and Ubuntu to lose their bootloaders.

---

### Post by TheFu on 2015-09-25
fsarchiver - backs up the file system contents, not the partition, but all the contents OF the partition.

But ... I'd use Windows tools to resize that smaller and use gparted to resize the Ubuntu partition(s) larger.  Be certain to have a full backup before starting **any** partitioning.  That applies for both Windows AND Linux.

---

