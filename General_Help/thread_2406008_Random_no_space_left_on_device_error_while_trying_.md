---
title: "Random no space left on device error while trying to unzip a large number of files?"
date: 2018-11-14
forum: General Help
---

### Post by somdyuti on 2018-11-14
Hi, 

I have been encountering a peculiar problem with Ubuntu 16.04. When I try to unzip a large number of files (around 12 million) to the same directory, I am getting ```
 Cannot create file, no space left on device
``` error for some files randomly; the error does not break the unzip process however, i.e. after throwing the above error for a particular file, it continues to unzip the others and again throws the same error for another file after a random time. All files are however of the same size. I am trying the following command for unzip:

```
 unzip -j '*.zip' -d ../Data 
```

I have around 2000 zip files which I want to unzip to the same directory as above. Also, strangely, if I split the zip files into two sets and unzip them in different directories they work without the above error - the error props up only when I try to unzip everything to the same directory. Why is this happening? 

Below is what I get with ```
df -i
```

```
udev             4106534      537  4105997    1% /devtmpfs            4112889      763  4112126    1% /run
/dev/sda2      119971840 41460479 78511361   35% /
tmpfs            4112889      133  4112756    1% /dev/shm
tmpfs            4112889        5  4112884    1% /run/lock
tmpfs            4112889       16  4112873    1% /sys/fs/cgroup
/dev/loop5         44739    44739        0  100% /snap/vlc/555
/dev/loop3         12783    12783        0  100% /snap/core/5742
/dev/loop4         12783    12783        0  100% /snap/core/5662
/dev/loop2         12783    12783        0  100% /snap/core/5548
/dev/loop1         38344    38344        0  100% /snap/vlc/190
/dev/loop0         45405    45405        0  100% /snap/vlc/365
/dev/sda1              0        0        0     - /boot/efi
tmpfs            4112889       30  4112859    1% /run/user/1000



```

and with ```
df -h
```

```
udev             16G     0   16G   0% /devtmpfs           3.2G   26M  3.2G   1% /run
/dev/sda2       1.8T  1.1T  650G  62% /
tmpfs            16G   50M   16G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/loop5      196M  196M     0 100% /snap/vlc/555
/dev/loop3       88M   88M     0 100% /snap/core/5742
/dev/loop4       88M   88M     0 100% /snap/core/5662
/dev/loop2       88M   88M     0 100% /snap/core/5548
/dev/loop1      181M  181M     0 100% /snap/vlc/190
/dev/loop0      198M  198M     0 100% /snap/vlc/365
/dev/sda1       511M  3.4M  508M   1% /boot/efi
tmpfs           3.2G   60K  3.2G   1% /run/user/1000



```

Thus, it seems that I have both physical memory and inodes available. Also, it has no problem in unpacking to another directory. Please suggest a fix or workaround for this issue. Thanks.

---

### Post by TheFu on 2018-11-14
Could you have hit a file system limitation for a single directory?  Which file system?  Which directory?
Having over 1,000 files in a single directory is to be avoided. I try to keep it under 500.

BTW, there is no need to ever show "loop" mounts unless the issue is directly connected to either a loop or snap.

---

### Post by HermanAB on 2018-11-15
Hmm, '12 million' of anything, is no small number.

Your file system may run out of inodes.  The processor may run out of RAM to store all the data structures while unzipping.

[https://stackoverflow.com/questions/17537471/what-is-the-max-files-per-directory-in-ext4](https://stackoverflow.com/questions/17537471/what-is-the-max-files-per-directory-in-ext4)

As explained in the above link, use 'df -i' to see what your file system can handle.

---

### Post by TheFu on 2018-11-15
```
/dev/sda2      119971840 41460479 78511361   35% /
```
shows there are 78M inodes available.  The OP posted it.

---

### Post by HermanAB on 2018-11-15
And how many inodes in /tmp?

---

### Post by TheFu on 2018-11-15
> **HermanAB said:**
> And how many inodes in /tmp?

Looks like 78M.

These are all good questions.  But the best answer really is to limit the number of files in a single directory to be less than 1,000.  If we look at how email spool or squid proxy directories  are setup, then we can see they use a tree structure to prevent huge numbers of files in any single directory.  This isn't by accident.

---

### Post by HermanAB on 2018-11-16
Ive had tens of thousands of files in a directory, but millions no.

---

