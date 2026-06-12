---
title: "Out of space message when there is space"
date: 2014-08-05
forum: General Help
---

### Post by Yahoé on 2014-08-05
On an Acer C720 2 GB RAM, 32 GB SSD, I use to run Lubuntu 14.04, and it worked OK. I added the Ubuntu Desktop to have access to Unity and started to have Out of space messages against /home, but every time I checked there was space.

I decided to Install Ubuntu 14.04 clean, formatting / in the process, /home being on a different partition that was not formatted in the process. Unfortunately, the Out of messages were present after the new install, but again when I checked space was available. Messages would be for about 800 MB left, 250 MB left, 70 MB left, but checking returned GBs of free space.

df returns :
/dev/sda2             9711776  6050600    3144792  66% /
none                        4        0          4   0% /sys/fs/cgroup
udev                   949664        4     949660   1% /dev
tmpfs                  192088     1100     190988   1% /run
none                     5120        0       5120   0% /run/lock
none                   960436      156     960280   1% /run/shm
none                   102400       64     102336   1% /run/user
/dev/sda3            21251956 13745240    7506716  65% /home

There is a 1024 MB swap file in /mnt. Right now, after the last message.
RAM is used at 44.6 %, Swap at 36.2 %.

Any idea what is happening, is there a log I can check to help understand what is happening?

---

### Post by Yahoé on 2014-08-05
I just realized that after opening Chromium (running two Gmail tabs), my available space in home jumps from 8.2 GB free to 147 MB free.
What is this? Running the same version of Chrome in Lubuntu 14.04 did not result in this problem.

---

### Post by Yahoé on 2014-08-07
I further investigated the issue and found out that using Chromium, Opera and Thunderbird to access my Gmail account resulted in over 7 GB to disappear from my home directory, to be released again upon closing the Gmail session. Still don't know how though as I wasn't able to find any particular file or folder taking that space.
Interestingly enough I can access and use my Gmail account from Firefox without considerable changes to my available space.
I would still like to understand why that is if anyone as a clue.

---

