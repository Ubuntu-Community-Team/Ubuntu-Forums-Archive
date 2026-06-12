---
title: "Different Partitions but all files always go to root and no more space..."
date: 2013-02-20
forum: General Help
---

### Post by rojas70 on 2013-02-20
Hi, 

I have a different partion for root and for home:

df -h
Filesystem      Size  Used Avail Use% Mounted on
**/dev/sda7        14G   13G  641M  96% /**
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  920K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  156K  3.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda5       114M   98M  9.8M  91% /boot
**/dev/sda8       409G   57G  332G  15% /home**

But the filesystem also contains /home inside of root /.

So I cannot figure out how to actually put my files in /home or /home/username/Documents without it filling up root.

Please help!

---

### Post by codemaniac on 2013-02-20
Moved to its own thread.

Cheers and best of luck!! :)

---

### Post by vanadium on 2013-02-20
> But the filesystem also contains /home inside of root /.
In the directory structure, /home indeed is a directory under the root directory (/)

Although home lives as a directory within the root directory, the actual data in home reside on a different partition. this is shown by the output of your mount command:
```

/dev/sda8 409G 57G 332G 15% /home

```
Your sda7 is the partition where most of your system data reside. However, another volume, sda8 is mounted to the home directory. Because of that, any data under /home reside on sda8.

Linux is a very user friendly system: the end user does not have to see or to care on what physical partition or drive the data are.

Your 14 G root partition is quite full, though. Typically, the linux system files do not need so much. I have a 9,3 G root, and 6.1 G is used.
One reason might be temp files: /tmp and /var/tmp by default reside on the root partition. Another reason might be that there are data in the root account. The home directory of root is /root. Another possibility is that there is still data under /home on the root partition. Once another volume is mounted on that directory, you would see the data on the other volume, and not anymore the "original" data.

---

### Post by Impavidus on 2013-02-20
Your /boot is quite full too. It seems like it holds three kernels right now and cannot contain a fourth, so you'll get an error message at the next kernel update. Use your favorite package manager to uninstall the oldest of the three. Its name is linux-image-<some version>.

Other things that can fill up your root partition are log files, located in /var/logs. It you've some faulty configuration that creates a bunch of error messages every second they may grow fast. Also, some programs need a lot of data in /usr/share. Typically that directory is quite small, but depending on the software you've installed it may contain several GBs.

Use **du** to find out which directories contain most data.

---

