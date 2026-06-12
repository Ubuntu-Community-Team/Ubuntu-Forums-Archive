---
title: "/bin/sh: can't access tty"
date: 2006-12-26
forum: General Help
---

### Post by commodore on 2006-12-26
I get this error when starting Ubuntu:
"/bin/sh: can't access tty; job control turned off". I'm totally sure it's my fault. Maybe it's because I edited /etc/fstab. Earlier I also got "Mounting /proc on /root/proc failed; no such file or directory" with different things in place of /proc. I then modified /etc/fstab and now it only gives me the error I wrote about earlier.

---

### Post by bulldog on 2006-12-26
If you have the menu.lst in order and all pointing to the right partitions,then you have to look in fstab if this is the same as in menu.lst.

For example if your menu.lst stated to boot from (hd0,2) --> is hda3 ext3,you have to see if this partition is set up according this.
If there is hda3 listed as a vfat partition you're in trouble,till you fix it.

It has to be similar to each other.

Here's a great how to from bodhi.zazen about the fstab,

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

---

### Post by commodore on 2006-12-27
Lol never modify fstab! I just wanted to remove auto-mounting of other partitions. The graphical installer didn't allow me to disable it. I personally liked the non-graphical installer better in a lot of ways.

---

### Post by commodore on 2006-12-27
Everything's fine with GRUB. I now checked the partition's /dev and there are no hdds, hdas  or hdcs! How could that happen?? What should I do? Copy the ones on the LiveCD?

---

### Post by commodore on 2006-12-27
I installed Dapper insted. I'll start looking for a new distribution cause it seems Ubuntu doesn't work.

---

