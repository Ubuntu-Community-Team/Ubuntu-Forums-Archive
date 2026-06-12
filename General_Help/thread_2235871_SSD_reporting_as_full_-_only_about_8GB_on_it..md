---
title: "SSD reporting as full - only about 8GB on it."
date: 2014-07-23
forum: General Help
---

### Post by HereInOz on 2014-07-23
Hi All,

I have an interesting one in that my 120 GB SSD which is mounted as /, with another drive as /home, is reporting as full, but there is only about 8Gb of data on the drive.  I have done a fstrim, to no avail, and I have noticed that when I chekc the size of the /proc folder, it reports as 140 TB.

Clearly something is wrong with the file structure on the drive, or something similar, but I do not have the knowledge to correct it.  It is a EXT4 partition. If I can't fix it, it is a re-install perhaps.

Can someone assist.

---

### Post by Impavidus on 2014-07-23
Here are some ideas for trouble-shooting: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

/proc is a pseudo file system. Its size is meaningless.

---

### Post by yancek on 2014-07-23
When you say "another drive as /home" do you mean another partition for /home on the same drive or on a separate physical drive?
Post the output of: sudo  fdisk -l  as well as sudo parted -l (Lower Case Letter L in both commands)
If the partitions are mounted, the command:  df -h will give useful information.

---

### Post by HereInOz on 2014-07-23
Thanks good people.  I may have found the culprit in a .Trash-0 directory in the root.  I am still checking things out but it looks like a lot of rubbish was in that directory.  Thank you for the info.

Yes it is a second physical drive.  I use the SSD for / and a 1TB drive for /home.

---

### Post by HereInOz on 2014-07-23
Yep, that was it.  All good now.  Many thanks again.

---

