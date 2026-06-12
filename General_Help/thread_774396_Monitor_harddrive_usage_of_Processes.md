---
title: "Monitor harddrive usage of Processes"
date: 2008-04-29
forum: General Help
---

### Post by honeydew on 2008-04-29
Is it possible to monitor hard drive usage in relation to processes.  IE if a few things were running, firefox, gedit, and beagled.  To show these guys in a top like interface which may look like

beagled
firefox
gedit

(example above based on what I think would be putting more strain on the hard drives)

I searched quite a bit yesterday but wasnt able to come up with anything.

---

### Post by aheckler on 2008-04-29
There's the System > Administration > System Monitor then the Processes tab, but I'm not sure if this is exactly what you're looking for.

---

### Post by bingoUV on 2008-04-29
1. Kill syslogd process. It tampers with our observations. 

 2. ```
 sudo echo 1 > /proc/sys/vm/block_dump 
```  3. Now run dmesg every now and then to know which process is abusing your beloved disk.

---

### Post by honeydew on 2008-04-29
oh cheers bingo!  One must wonder, what other nifty tricks do you have up thoose sleeves of yours.

---

### Post by honeydew on 2008-04-29
just a quick question.. do you know what this might be called on legacy redhat machines.. only thing in the sys/vm folder is 

-bash-2.05b$ ls
bdflush  kswapd  max_map_count  max-readahead  min-readahead  overcommit_memory  page-cluster  pagetable_cache

---

### Post by bingoUV on 2008-04-29
No idea. Must be an ancient system. Post the kernel version here and someone here will be able to help you.

---

### Post by honeydew on 2008-04-29
Linux 2.4.20-30.9smp #1 SMP Wed Feb 4 20:36:46 EST 2004 i686 i686 i386 GNU/Linux

---

