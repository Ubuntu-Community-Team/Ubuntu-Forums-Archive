---
title: "package update 12.04 disk space problem"
date: 2013-09-29
forum: General Help
---

### Post by alainhenry on 2013-09-29
Sorry, I need some help here: 
I had an error during the last update of 12.04. Some package could not be updated, and the system told me to run dpkg --configure -a

Running it, I get an error:
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: nno space left on device

If I run Synaptic, I get the message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Using apt-get clean or a similar command gives me the same message.

I assume either my root or my boot partition is full (I have a separate /home). How can I clean it ?

Thanks

---

### Post by Bashing-om on 2013-09-29
alainhenry; Hi !

Possible to be a number of causes;
The following command is useful for finding out which directories are using all your space...
```

du -h --max-depth=1 | sort -hr

```
once known .. corrective action can be taken.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by alainhenry on 2013-10-01
I got space enough, it's actually an inode problem.  See [http://ubuntuforums.org/showthread.php?t=2177778]("http://ubuntuforums.org/showthread.php?t=2177778http://")

---

### Post by Bashing-om on 2013-10-01
alain; Hi !

As stated in the referenced thread, all you can do in a situation of no more inodes is delete any and all un-needed files to free up some inodes.

If this were a production machine, one would of course (re)partition and use some tools to increase the allocation of inodes within  a larger partition.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by alainhenry on 2013-10-02
Yes, thanks! And thanks to the mighty Forum!

---

