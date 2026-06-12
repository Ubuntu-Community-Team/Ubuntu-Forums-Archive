---
title: "Downsizing partitions and using free space..."
date: 2005-08-16
forum: General Help
---

### Post by danf_1979 on 2005-08-16
Hi to all:
I have some partition size problems. When I installed Ubuntu, I did the following:
/ with 9.11 GB
/var with 1.86 GB
/usr with 7.17 GB
/home with 93.22 GB

Well, now my used space is like this:
/ only 2% used
/var only 10% used
/usr only 27% used

I want to modify the partition sizes to give some more space to /home partition. Is this possible or do I have to reinstall to make this changes? I did try with Gparted, but is said that I should unmount the partitions first... but they are in use. 
I want to have something like this:
/ with 0.6 GB
/var with 0.8 GB
/usr 6 GB
/home The rest GB

So I must downsize /, /var and /usr and then use the free space to upsize /home...
Is there anyway I can do this?
Thanks in advance

---

### Post by jasmuz on 2005-08-16
You could use a live cd with Gparted to resize them. (knoppix has it by default, in Ubuntu it must be downloaded)

---

### Post by danf_1979 on 2005-08-16
Ok, so I did it.
I downsized all mentioned partitions, BUT, I cant upsize /home!!! When the program asks for the new size of /home, I only can specify lower values... 
What can I do?? Because i *do* have some free unpartitioned space...

---

### Post by danf_1979 on 2005-08-16
I'm using Reiserfs

---

### Post by danf_1979 on 2005-08-16
Sorry for the 3rd post... but I'm a bit confused. I thought it could be reiserfs... but I have some small partitions in reiserfs that I CAN make bigger... dont know why in /home I cant do that. Any help appreciated

---

### Post by heimo on 2005-08-16
I believe partition needs to be continuous. I haven't played with Gparted, so I may be mistaken, but I think your situations requires "moving" the other partitions until the free space is next to the one you're growing.

---

### Post by OwlManAtt on 2005-08-16
In the future, you should consider partitioning your disks at installation time and using LVM on them. The Ubuntu installers allows for you to set up LVM along with partitions. That would make resizing your partitions much easier. I plan to use it next install I do.

[http://www.tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html](http://www.tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html)

---

