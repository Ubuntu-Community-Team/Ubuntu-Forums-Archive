---
title: "FYI: kernel 4.0 compile: disk space and time needed"
date: 2015-02-24
forum: General Help
---

### Post by sanderj on 2015-02-24
FYI:

I compiled/made linux kernel 4.0.0-rc1 on my HP Stream 13 (2GB RAM, dual core Intel Celeron N2840) based on the clear instruction on [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild), and this is my experience:

After the "git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git" the disk in use in the separate kernel directory: 1691 MB

During the make/compile, the disk space in use went up to 15674 MB. So: **more than 15GB** ... 

Total compile time was: 299 minutes, or 5 hours. Quite long, probably caused by my slow CPU and slow disk.

---

### Post by sanderj on 2015-02-25
Result on an Intel Core i3-2310M CPU @ 2.10GHz with harddisk and 4GB RAM:

Linux 4.0.0-rc1 compile took 140 minutes, so 2 hours and 20 minutes

---

### Post by Doug S on 2015-02-25
By default, and I do not know why, the Ubuntu kernel config files have debug enabled. And yes, that takes much longer to compile. I always use the Ubuntu kernel config file, but also always turn the debug off:```
scripts/config --disable DEBUG_INFO
```For these differences:```
doug@s15:~/temp-k-git-3.10rc4/linux$ diff .config-4.0.0-040000rc1-generic .config
3c3
< # Linux/x86_64 4.0.0-040000rc1-generic Kernel Configuration
---
> # Linux/x86 4.0.0-rc1 Kernel Configuration
7454,7458c7455
< CONFIG_DEBUG_INFO=y
< # CONFIG_DEBUG_INFO_REDUCED is not set
< # CONFIG_DEBUG_INFO_SPLIT is not set
< CONFIG_DEBUG_INFO_DWARF4=y
< # CONFIG_GDB_SCRIPTS is not set
---
> # CONFIG_DEBUG_INFO is not set
```Your compile should be faster and the larger dbg file will not be created. Example (from the last time I forgot to disable debug)```
-rw-r--r--  1 doug doug 40944164 Nov 30 18:17 linux-image-3.18.0-rc7-250_3.18.0-rc7-250-180_amd64.deb
-rw-r--r--  1 doug doug 75607226 Nov 30 18:21 linux-image-3.18.0-rc7-250-dbg_3.18.0-rc7-250-180_amd64.deb
```By the way, there is always a [thread]("http://ubuntuforums.org/showthread.php?t=2266435") over on the [Ubuntu Development Version]("http://ubuntuforums.org/forumdisplay.php?f=427") sub-forum for the latest Release Candidate Kernel, if you care to chime in there.

---

### Post by sanderj on 2015-02-25
Very interesting and helpful!

```
git/linux$ grep CONFIG_DEBUG_INFO .config
CONFIG_DEBUG_INFO=y
# CONFIG_DEBUG_INFO_REDUCED is not set
# CONFIG_DEBUG_INFO_SPLIT is not set
CONFIG_DEBUG_INFO_DWARF4=y
```

I will rerun with debug turned off.

Thank you.

---

### Post by Doug S on 2015-02-25
By the way, my last build took 22 minutes and 52 seconds on an i7-2600K CPU @ 3.40GHz (Turbo to 3.8):```
real    22m51.623s
user    100m20.292s
sys     5m4.484s
```

---

### Post by sanderj on 2015-02-25
> **Doug S said:**
> By the way, my last build took 22 minutes and 52 seconds on an i7-2600K CPU @ 3.40GHz (Turbo to 3.8):```
real    22m51.623s
user    100m20.292s
sys     5m4.484s
```

Thanks.

I wonder how Phoronix ([http://www.phoronix.com/scan.php?page=news_item&px=MTAyNjU](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNjU)) achieved a linux kernel compile of 1 minute with an Intel Core i7 3960X. Or is the Intel Core i7 3960X 22 times faster than your i7? ;)

---

### Post by Doug S on 2015-02-25
> **sanderj said:**
> I wonder how Phoronix ([http://www.phoronix.com/scan.php?page=news_item&px=MTAyNjU](http://www.phoronix.com/scan.php?page=news_item&px=MTAyNjU)) achieved a linux kernel compile of 1 minute with an Intel Core i7 3960X. Or is the Intel Core i7 3960X 22 times faster than your i7? ;)
[LIST]
[*]They are using a solid state drive (likely the biggest difference). I am using a regular hard drive. 
[*]They have 12 threads. I have 8. 
[*]The article was written in 2011. On my same computer the kernel used to take about 11 minutes to compile sometime in 2012. 
[*]They may have trimmed down what they compile to just what they need (I didn't read in detail), The Ubuntu kernel config results in compiling most everything. 
[/LIST]
 
Edit: Here is my build time, building on an SSD:```
real    20m47.611s
user    118m36.304s
sys     6m7.824s
```Which I made no attempt to optimize.

---

### Post by sanderj on 2015-02-26
Again on my  Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz, now with "# CONFIG_DEBUG_INFO is not set":

```
real	167m2.924s
user	253m33.108s
sys	23m43.864s
```

So: 2 hours plus 47 minutes. Much better than the original 5 hours. :D

And maybe even more important: 'du' shows only 3460 MB disk usage (instead of the 15GB)

---

