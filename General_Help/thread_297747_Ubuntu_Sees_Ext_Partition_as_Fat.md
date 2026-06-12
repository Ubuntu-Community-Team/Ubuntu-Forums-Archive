---
title: "Ubuntu Sees Ext Partition as Fat"
date: 2006-11-11
forum: General Help
---

### Post by Adanufgail on 2006-11-11
Because Fat32 does not support over 4 GB files, I wished to convert it to ext3. I did so first with Ubuntu's Disk Manager. Ubuntu was unable to remount the disk, seeing it as a Windows Fat Partition. I tried rebooting, with no luck. I then used my hd's format disk to reformat it to fat32, and Ubuntu saw it again. Using the console fdisk, I saw the same results. I then tried using a knoppix disk I had to do it, and once again Ubuntu said it was Fat and could not mount it.

Any help would be appreciated,
Michael

---

### Post by catlett on 2006-11-11
When you change the format of a file, you need to change the entry for it in /etc/fstab. That file tells the computer which partition to mount, what filesystem it is and where to mount it. Althjough you changed the format to ext3, the system still sees it as fat.
It is probably easiest to point you to Aysiu's tutorial for mounting a linux partition [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
The one difference between the how to and your situation is your /etc/fstab aleady has an entry for that partition. Either erase it or modify it to look like the line in the how to.

---

### Post by Adanufgail on 2006-11-11
Thanks, worked like a charm.

---

