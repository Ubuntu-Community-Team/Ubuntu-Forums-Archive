---
title: "Error Message : Diskfull because of hidden files in 13.10"
date: 2014-03-11
forum: General Help
---

### Post by V_R_RAJITH on 2014-03-11
This is second time I am getting troubled in Disk Space problem.
There are 200 GB space is net available in my Partition.
27 GB used by the whole sum with ..but when on the properties seems 185 GB used 100% ..

I think some hidden files like backup extensions may cause this
How do I purge these unwanted files & to prevent the future threat..???

Please help me...

---

### Post by ajgreeny on 2014-03-11
Let's see the output of **df -h** in terminal to see more detail.

---

### Post by V_R_RAJITH on 2014-03-11
linux@linux-Lenovo-U310:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb5       196G  172G   14G  93% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           391M  1.2M  389M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  536K  2.0G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sdb1       200M   34M  167M  17% /media/linux/SYSTEM_DRV

I have recovered 12 GB from Thunderbird..
IMAP google

thanks - ajgreeny

---

### Post by ibjsb4 on 2014-03-11
You can also run a check for folders over !g in size.

```
[COLOR=DarkRed]**sudo find / -name '*' -size +1G**[/COLOR]
```

step #4

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by ajgreeny on 2014-03-11
Yes, it would be very useful to know what is using all that 172GB of space.  Have a look with Disk Usage Analyser and scan the whole filesystem; it may give us some clues.

In the left hand pane there will be a listing of the main system folders which will show their size and should help us see where all the space is being used.  See screenshot.

---

