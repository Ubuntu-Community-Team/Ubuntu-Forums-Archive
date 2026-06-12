---
title: "Periodic File System Checking (fsck) Disabled in 13.10"
date: 2013-10-28
forum: General Help
---

### Post by Dennis N on 2013-10-28
Just a notice as information to users:

Lubuntu 13.10 and possibly other 13.10. Automatic periodic filesystem check (fsck) is disabled. This has been the case since 12.04 release.

**To check if fsck is disabled, and check the current and maximum mount count (here on sdb8):**

```
dn@Roxanne:~$ sudo dumpe2fs -h /dev/sdb8 | grep -i "mount count"
[sudo] password for dn: 
dumpe2fs 1.42.8 (20-Jun-2013)
Mount count:              10
Maximum mount count:      -1

```
-1 as "Maximum mount count" tells you it is disabled, no checking will be done.

[B]To fix and set check interval to 40 mounts (here on sdb8):
[/B]
```
dn@Roxanne:~$ sudo tune2fs -c 40 /dev/sdb8
[sudo] password for dn: 
tune2fs 1.42.8 (20-Jun-2013)
Setting maximal mount count to 40
```

Background Information:

> In Ubuntu (and most Linux distributions), the file system on your system is checked periodically when your computer boots using "fsck", ("file system consistency check") to detect errors and correct them. You will see a notification on the splash screen when this occurs together with  progress as a percent. The time required is small - generally about 1 minute. By default, in the past this checking was done about every 30 boots (it varied slightly). Currently, this checking is disabled.

---

### Post by ajgreeny on 2013-10-28
Does anyone know why this was taken out of the default settings?

 I always felt comforted by the filecheck when it happened and I have mine now set to check every two months by changing the command of Dennis N above to [code]sudo tune2fs -i 2m /dev/sda4[code]The choice is yours but it makes sense to me to run this check occasionally.

---

### Post by mörgæs on 2013-10-28
Do you have a link please explaining which kind of errors fsck can help preventing / avioding? It will help people to judge if they should enable the check.

---

### Post by SuperFreak on 2013-10-28
Where would one find log files showing output of fsck and does it automatically do corrections or is it just a check of problems?

---

### Post by Dennis N on 2013-10-28
> **SuperFreak said:**
> Where would one find log files showing output of fsck and does it automatically do corrections or is it just a check of problems?

The logs are at: /var/log/fsck

As to corrections, it's my understanding that if errors are found, fsck will offer to make corrections. You need to confirm (y/n).
In my case, I have never seen any problems reported by the automatic checks, so I have no first hand account of this.
See the man page for more technical details if you are interested. There are also lots of articles to be found on the web.

---

### Post by SuperFreak on 2013-10-28
> **Dennis N said:**
> The logs are at: /var/log/fsck

As to corrections, it's my understanding that if errors are found, fsck will offer to make corrections. You need to confirm (y/n).
In my case, I have never seen any problems reported by the automatic checks, so I have no first hand account of this.
See the man page for more technical details if you are interested. There are also lots of articles to be found on the web.

There are two files at /var/log/fsck  "checkroot" and " checkfs" and both files have one entry "(Nothing has been logged yet.)"
I have checked this a number of times in the past including right after a fsck scan. 
Surely more info should be in these logs or have I somehow disabled the logging function of fsck?

---

### Post by SuperFreak on 2013-10-28
And here is why there is nothing in the log [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644")

seeing as this bug dates back to Jaunty it would be unlikely that it will be addressed. What is the value of fsck if nothing is logged?

---

### Post by Dennis N on 2013-10-28
> **mörgæs said:**
> Do you have a link please explaining which kind of errors fsck can help preventing / avioding? It will help people to judge if they should enable the check.

Here is one of many links:

[http://webtools.live2support.com/linux/fsck.php](http://webtools.live2support.com/linux/fsck.php)

According to this, fsck stands for "file system consistency check". It does not check the condition of the hard disk, but the condition of the file system on the hard disk.

Since it takes so little time to complete, nowadays only a minute or so, there seems to be nothing to be gained and potentially something to lose by not running it. (my opinion).

---

### Post by Dennis N on 2013-10-28
> **SuperFreak said:**
> There are two files at /var/log/fsck  "checkroot" and " checkfs" and both files have one entry "(Nothing has been logged yet.)"
I have checked this a number of times in the past including right after a fsck scan. 
Surely more info should be in these logs or have I somehow disabled the logging function of fsck?

To tell the truth, I have never had a reason to look at them, since I have never had errors reported. This new 13.10 system says the same as yours. I assumed that was because none had been done yet (only 10 mounts). I will look at an older installation and see what that system says.

---

### Post by Dennis N on 2013-10-28
> **SuperFreak said:**
> And here is why there is nothing in the log [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/513644")

seeing as this bug dates back to Jaunty it would be unlikely that it will be addressed. What is the value of fsck if nothing is logged?

Seems that it cound still detect and offer to correct errors if any were found, log file or not. It's interactive.

EDIT:

I find fsck logs are now part of the **boot.log**:

```
fsck from util-linux 2.20.1
Lubuntu-1210: clean, 304033/1921360 files, 2807004/7680000 blocks
```

---

### Post by Dennis N on 2013-10-28
Checked for logs on older systems. Only Ubuntu 8.04 has an entry - see below (apparently they are made daily on startup). The others (like 12.04) say "nothing logged yet" as the bug says. But, as I said, the fsck program is interactive and should still perform its check and if warranted, repair functions so I will keep it activated. I see nothing to gain by leaving it disabled, and plenty to lose. I takes only a minute or so extra time every 40 boots as I have it set.

Ubuntu 8.04 fsck log entry (there are none for past days, just the current session):

```
dn@dell-desktop:/var/log/fsck$ cat checkroot
Log of fsck -C3 -a -t ext3 /dev/sda3 
Mon Oct 28 19:55:21 2013

fsck 1.40.8 (13-Mar-2008)
/dev/sda3: clean, 413455/4800512 files, 13505578/19200038 blocks
```


EDIT: In newer releases, this information is now part of **/var/log/boot.log**
Boot log lines from Lubuntu 12.10:
```
fsck from util-linux 2.20.1
Lubuntu-1210: clean, 304033/1921360 files, 2807004/7680000 blocks
```

This partition checked has a label which is why you see "Lubuntu-1210" (the label) rather than /dev/sda1

---

### Post by drmrgd on 2013-10-29
Interesting.  Running 12.04 here, and it seems it's turned off by default on my system too:

```

$ sudo dumpe2fs -h /dev/sdc3 | grep -i "mount count"
dumpe2fs 1.42 (29-Nov-2011)
Mount count:              38
Maximum mount count:      -1

```

Here's something odd, though.  That's the partition for my Home dir.  If I look at root, I see that it's been mounted 14 fewer times!

```

$ sudo dumpe2fs -h /dev/sdc2 | grep -i "mount count"
dumpe2fs 1.42 (29-Nov-2011)
Mount count:              24
Maximum mount count:      -1

```

How is that possible?

Anyway, I think I'll turn this on too.  It is always nice knowing that the filesystem is being kept in good condition.

---

### Post by Dennis N on 2013-10-29
I found that fsck log is now part of  **var/log/boot.log**

Example from this machine's boot.log, lines 1-2:

```
fsck from util-linux 2.20.1
Lubuntu-1210: clean, 304033/1921360 files, 2807004/7680000 blocks
```

---

