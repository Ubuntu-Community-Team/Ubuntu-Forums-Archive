---
title: "Need to make Shared folder bigger"
date: 2020-01-25
forum: General Help
---

### Post by cj8281 on 2020-01-25
Dell poweredge T110 II server with a single 500gb sata drive.
Using Ubuntu 18.04 server with KDE desktop, loaded Samba and created a shard folder.  Was able to access the shared folder from my windows computer and made a couple of directories and started moving files.  I moved almost 17 gb of files over and when I was going to move the next set of files over it said that it needed more room.  How do I find out how much room I have on the hard drive?  Are there limits to folder sizes and if so do I have to make more folders so I can move all of my files onto my server?  Is there a Ubuntu for dummies somewhere on here that I can read and learn how to do this stuff?  I have googled this and haven't found anything close to what I am looking for.

---

### Post by therealdps on 2020-01-25
```
df -h
``` will give you a human readable output of your disk usage and list of partitions and whatnot. It sounds like maybe your home directory is full, but I am not 100% sure. After you check out the df command, report back. In the meantime, check out these two links. They have to do with increasing the sizes of your /home and your /root directories.

---

### Post by cj8281 on 2020-01-25
Ok, I ran that in Konsole and this is the output:

```
Filesystem                                              Size  Used   Avail Use%    Mounted on
udev                                                    7.8G     0     7.8G   0%      /dev
tmpfs                                                   1.6G  2.9M     1.6G   1%      /run
/dev/mapper/ubuntuServer--vg-root                        29G   25G     2.3G  92%      /
tmpfs                                                   7.9G   41M     7.8G   1%      /dev/shm
tmpfs                                                   5.0M     0     5.0M   0%      /run/lock
tmpfs                                                   7.9G     0     7.9G   0%      /sys/fs/cgroup
/dev/sda1                                               511M  6.1M     505M   2%      /boot/efi
tmpfs                                                   1.6G     0     1.6G   0%      /run/user/122
tmpfs                                                   1.6G   12K     1.6G   1%      /run/user/1000
clay@ubuntuServer:~$ 
```
Took me a minute to straighten the info out from Konsole, it didn't paste as nice of spacing on here.  Hope this helps.
I don't see anything the size of my shared folder which now has 16gb of stuff in it and nothing the size of the total 500gb.

---

### Post by cj8281 on 2020-01-25
OK, it looks like none of my spacing helped out in the quote from Konsole.

Also, I don't see 2 links in your post, sorry.

Poking around in Dolphin, I found that it lists the hard drive as 28.8 gb under devices.   Does this mean the rest of the hard drive is unformatted and unused?  If so, how do I go about formatting it and moving the files to that portion of the drive?  I eventually want to set up the OS on a 40 gb ssd that a friend just give me and run the 500 gb as the information holder.

---

### Post by deadflowr on 2020-01-25
Best to use code tags for terminal output as it retains the proper formatting.
I've fix that for you.

Code tag primer here: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

