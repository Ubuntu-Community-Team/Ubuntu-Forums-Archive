---
title: "Where to learn about Linux filesystem internals"
date: 2014-02-27
forum: General Help
---

### Post by lemiant on 2014-02-27
I'm currently working on a project that involves processing a large number of files (~100,000). I have discovered that the main bottleneck in the program is file IO and I'm trying to pursue ways of speeding that up. The program is currently in Python, but I'm open to using C as well. Throughout this process I've done a metric ton of googleing and it's actually quite hard to find out about the internal workings of the linux filesystem. For example I want to know how linux converts file paths to inode numbers. If it does so by opening each directory in the path, finding the appropriate entry and repeating until it has travesed to the requested file then that operation could be contributing a lot of time to opening my relatively small files in a deep directory structure. In that case I might want to cache all the inodes on my way by during the first traversal and then use those to directly access files.
What I want to know is, do you know of any good forums or resources to find out about the internal workings of the filesystem and ways to optimize accessing it?

Thanks,

- Alex

---

### Post by Habitual on 2014-02-27
[http://www.tldp.org/](http://www.tldp.org/)

---

### Post by tgalati4 on 2014-02-27
You should instrument your code and see what the bottlenecks are.  A guru on system performance:  [https://www.socallinuxexpo.org/scale12x/presentations/what-linux-can-learn-solaris-performance-and-vice-versa](https://www.socallinuxexpo.org/scale12x/presentations/what-linux-can-learn-solaris-performance-and-vice-versa)

It's doubtful that you will change the kernel to support your workload.  You might adjust scheduling and change some tuning parameters, but that can be done in user space or at boot time with the correct switches.  But first, you need a handle on what real-time bottlenecks exist on your system with your hardware setup.  Simply getting faster disks or more RAM or a RAID1 or a different file system like btrfs might improve your throughput.

Efforts to "outthink" the kernel often cause other problems.  So first, perform the analysis, share the results, and then meaningful tweaks will be evident.

More reading:  [https://help.ubuntu.com/community/DiskPerformance](https://help.ubuntu.com/community/DiskPerformance)

---

### Post by coldraven on 2014-02-27
This is a bit beyond me but I found this here: [http://kernelnewbies.org/Ext4#head-c212d1622081e592caa73b9e14511cee45fb989b](http://kernelnewbies.org/Ext4#head-c212d1622081e592caa73b9e14511cee45fb989b)
> [h=2]2.7. Fast fsck[/h]  Fsck is a very slow operation, especially the  first step: checking all the inodes in the file system. In Ext4, at the  end of each group's inode table will be stored a list of unused inodes  (with a checksum, for safety), so fsck will not check those inodes. The  result is that total fsck time improves from 2 to 20 times, depending on  the number of used inodes ([http://kerneltrap.org/Linux/Improving_fsck_Speeds_in_Ext4](http://kerneltrap.org/Linux/Improving_fsck_Speeds_in_Ext4)).  It must be noticed that it's fsck, and not Ext4, who will build the  list of unused inodes. This means that you must run fsck to get the list  of unused inodes built, and only the next fsck run will be faster (you  need to pass a fsck in order to convert an Ext3 filesystem to Ext4  anyway). There's also a feature that takes part in this fsck speed up -  "flexible block groups" - that also speeds up filesystem operations.

And searching for "ext4 inode" I found this article on using mke2fs to optimise your file system:
[http://www.eskimo.com/linux/filesys.html](http://www.eskimo.com/linux/filesys.html)

> I use a directory index because the speed up of access in large  directories is worth the minor increase in space the index consumes.

---

### Post by SeijiSensei on 2014-02-27
How big are these files?  What if you moved a number of them onto a RAM disk and processed them from there rather than reading and writing to hard drive for each file?  Something like:

Move 1000 files to ramdisk
Process those files
Copy results back to disk storage
Rinse and repeat

---

