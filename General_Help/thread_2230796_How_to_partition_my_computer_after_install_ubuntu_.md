---
title: "How to partition my computer after install ubuntu 14.04LTS"
date: 2014-06-21
forum: General Help
---

### Post by sivaraman_l on 2014-06-21
Hi,
I intalled ubuntu 14..4 LTS with full erase of windows operating system unfortunately. Now all the 450 GB hard disk has been combined into one. I cant able to create folder into that single disk. So anybody tell how to partition my disk space through ubuntu. 

Thanks in advance

---

### Post by bapoumba on 2014-06-21
I wont be able to thouroughly help you with that, someone will come along and will for sure. But one thing : if you want to be able to recover files that were on your computer before you installed ubuntu, please stop using it right now. Do you have another machine to follow instructions ?

---

### Post by sudodus on 2014-06-21
Welcome to the Ubuntu Forums :-)

Please describe with more details what is your problem and what you want!

- Is Ubuntu working or not?
- Do you want to get Windows back?
- Do you want some personal files back?

If you want something back after overwriting, avoid running the computer until you have a good plan. At least do not create or mount any partition on the internal drive. Otherwise you might cause even bigger damage to what might be possible to recover.

Please look at the following links. First a recent thread with a similar (but not exactly the same) problem. The some general tips.
[URL="http://ubuntuforums.org/showthread.php?t=2230578"]
3TB hard drive problem, what to do?[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
[/URL][https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by sivaraman_l on 2014-06-21
I want details about how do the partition after installing ubutu.

---

### Post by jal9904 on 2014-06-21
Use GParted. I don't know if it is preinstalled with ubuntu anymore, but if it isn't, get it in the ubuntu software center. GParted is a partition tool.

---

### Post by oldfred on 2014-06-21
You cannot use gparted from your working system as you cannot edit mounted partitions, but it is installed in the live installer version. And you may have to click on swap and swap off as the live installer usually mounts swap automatically.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

