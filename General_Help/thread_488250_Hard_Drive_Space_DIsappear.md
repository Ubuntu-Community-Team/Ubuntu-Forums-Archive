---
title: "Hard Drive Space DIsappear?"
date: 2007-06-29
forum: General Help
---

### Post by thuang on 2007-06-29
Hi, I installed ubuntu 7.04 in my old laptop a week ago. I encountered a weird problem today. about 10gb of my hard drive space is being used without me knowing. I opened disk usage analyzer and it shows 14.7GB is being used and 20.5GB is free. Then I did a Filesystem Scan, it only finds 4.1GB being.

My question is, where is the other 10.6GB?

How do I put a screenshot in the post?

---

### Post by meatpan on 2007-06-30
The difference might be related to assumptions made by the disk usage analysis tools.  Consider the output of the command, 'df -h' . The df command provides a summary of the total free space on each disk, as well as separate partitions.  Try running the command and seeing if the total numbers tie out to your expectations.

---

### Post by thuang on 2007-06-30
The result of df -h... 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   15G   19G  45% /
varrun                379M  120K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  144K  379M   1% /proc/bus/usb
udev                  379M  144K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile

It shows 15G is being used, while I only used 4.1G...10G of space is used without me being knowing this afternoon...Could it be something wrong with my harddrive?

---

### Post by merlinus on 2007-06-30
You might check ~/.trash and /.trash to see if deleted material is still residing on your disk.

-merlin

---

### Post by thuang on 2007-06-30
This is so weird...This afternoon, ubuntu told me I have 15M left in my hard drive. I restart the computer, ubuntu tell me I have 19G free. Now I restarted it again, I have 29.1G.

I don't know what caused it...but I got my 10G back.

Thank you for your reply, this forum is a great place. :D

---

