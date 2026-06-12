---
title: "mount disk space problem"
date: 2007-07-19
forum: General Help
---

### Post by liorc666 on 2007-07-19
well i installed ubuntu edgy before 2 days
(im quite exprinse with linux) i also upgrade to feisty and installed everything
and everything work just great my problem is when i installed edgy i choose 25 GB for / and 6 GB to /home , i didnt think about that i install Wine and such things in /home folder and now i got low space on /home and / still have lots of space how can i mount more space to /home? 

i also look in google and in the forum but i dunno what exactly too look for ...
i saw that  "df -h" command will show disk space

ailon@pc-ailon:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              25G  5.4G   18G  24% /
varrun                506M  132K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  104K  506M   1% /proc/bus/usb
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             5.7G  1.6G  3.8G  30% /home
/dev/sda1              21G   17G  3.7G  83% /media/hda1
/dev/sda2              30G   30G   84M 100% /media/hda2



(i have got 21GB on windows(c: ) partition and more 30GB in windows (d: ) partition whice is on the first hard disk (80GB HD) and my Linux is on the third partition in the same HD with 25GB , the home folder is on another HD with 6.5 GB and the swap is also there (ubuntu installation made it ))


there is something i can do to give more space to /home ? because my Steam takes lots of its space for games.


Thanks for helpers :)

---

### Post by phidia on 2007-07-19
Get the GParted live cd [here]("http://gparted.sourceforge.net/livecd.php"). Read the guides at that site for using it and you should be able to accomplish what you want.

---

### Post by liorc666 on 2007-07-19
oh , you mean to resize the big ext3 partition (/) and get some more to /home ?

well thanks i think i have got it !
gonna try :D

---

### Post by phidia on 2007-07-19
Yes resizing is what I meant I thought that's what you were asking. I hope it works for you. If you have any problems with resizing or using gparted post back here or create a new thread with the specifics of what is happening. Good luck :)

---

