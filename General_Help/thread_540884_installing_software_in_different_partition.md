---
title: "installing software in different partition"
date: 2007-09-02
forum: General Help
---

### Post by almon on 2007-09-02
my root partition is almost full and it happened to me many timed that i was not able to boot into my linux box due to less disk space
so is there a way to install softwares in different partition
for ex ...r there any parameters in apt-get command which install softwares in different partitions....

---

### Post by wjp.reg on 2007-09-02
Do you have some space you can resize using gparted or other partitioning software?  If not, perhaps you can add a hard drive and use LVM to extend your existing /root partition.

[Learning Linux LVM - Part 1]("http://www.gentoo.org/doc/en/articles/lvm-p1.xml")
[URL="http://www.gentoo.org/doc/en/articles/lvm-p2.xml"]
Learning Linux LVM - Part 2[/URL]

And here's a [howto LVM for ubuntu]("http://www.gerardsetho.net/web-programming/articles/article/resizing-ubuntus-root-file-system-with-lvm.html").

Good luck!

---

