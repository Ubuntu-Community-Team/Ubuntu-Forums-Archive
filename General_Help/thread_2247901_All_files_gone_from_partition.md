---
title: "All files gone from partition"
date: 2014-10-11
forum: General Help
---

### Post by ktz84 on 2014-10-11
Hi,

I have a partition for all my VMs and it is now showing no files. The computer had a power blip so not sure if that done anything or if was something else but in any case the partition itself is still there it is just that there is nothing on it. It is sdd4 and here is the output of fdisk -l

```
Disk /dev/sdd: 2000.4 GB, 2000394706432 bytes255 heads, 63 sectors/track, 243200 cylinders, total 3907020911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5bf994f7


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1       696322048  1720319999   511998976   83  Linux
/dev/sdd2      1720320000  3907020799  1093350400    f  W95 Ext'd (LBA)
/dev/sdd4            2048   696322047   348160000   83  Linux
/dev/sdd5      1720324096  3358724095   819200000   83  Linux
/dev/sdd6      3358726144  3890636799   265955328   83  Linux
/dev/sdd7      3890638848  3907020799     8190976   82  Linux swap / Solaris
```

I've unmounted the disk so as to try and maintain as best I can. Can you anyone advise what I can do to try and recover the data on that partition?

I'm using Ubuntu 14.04.1.

Thanks

---

### Post by sudodus on 2014-10-11
0. Restore from the backup if you have one.

1. The data is probably still sitting there, but the file system was borked by the power blip. ***Do not mount the damaged partition***. Every time you mount it, things will be harder to recover.

a. If you have another drive of at least the same size, make a cloned copy with ***ddrescue***, and try to recover data on the copy (reducing the risk). Let me know if you plan to try ddrescue, and I can help you with details.

b1. Use try to repair the file system with ***testdisk*** and ***gpart*** (not gparted). If it works, it is a fairly quick solution.

b2. If no luck with testdisk, try ***photorec***, which can recover data without a working file system. It works, but takes a long time. Try to focus on the most important files types, otherwise you might drown in data.

See this link for testdisk and photorec [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by ktz84 on 2014-10-11
Thanks sudodus. Unfortunately no backup so I'll give ddrescue a go to create that backup. I've made space on another partition which is a bit bigger than that partition and you help in doing that would be appreciated.

**Update:**
I have ddrescue now downloaded and built. I have also installed ddrescue-gui however it seems to want me to mount the partition because it's asking for device to image from and only showing current mounted options so not sure if I should mount or not given the warning about mounting the partition causing damage each time it mounts.

**Update2:**
I'm now running ddrescue. The command being used is:

```
sudo ddrescue -d -r3 /dev/sdd4 /media/eamonn/Backup/test.img /media/eamonn/Backup/test.logfile
```

It's about 1/3 or the way through.

---

### Post by sudodus on 2014-10-11
It looks good, you run it with a logfile ...

---

### Post by ktz84 on 2014-10-11
OK had a few thing to do this afternoon but back now and the ddrescue has run:

```
GNU ddrescue 1.19Press Ctrl-C to interrupt
rescued:   356515 MB,  errsize:       0 B,  current rate:   87556 kB/s
   ipos:   356515 MB,   errors:       0,    average rate:   63022 kB/s
   opos:   356515 MB, run time:    1.57 h,  successful read:       0 s ago
Finished                 
```

OK not sure what to do now?

---

### Post by sudodus on 2014-10-11
Well, you selected to save it to an (uncompressed) image file instead of a cloned partition or drive. There seems to be no error, so it should be OK.

It will be easier to work on the original drive. If you mess it up with testdisk, you can reverse the cloning process and restore the partition from the image file.

Please read the documentation at the website [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

***Download*** testdisk and photorec, ***or simply install them*** into your live system (an Ubuntu install DVD/USB drive?) and start working with ***testdisk***.

Testdisk can be installed by

```
sudo apt-get install testdisk
```

but I think you must download photorec.

I'm not expert, I think you can find out by using ***testdisk***, which options might help you. You can also find more tips and tutorials via the internet. Try more than once, do not give up too early! But if you have no luck, you must finally skip it and maybe try ***gpart*** and if necessary finally resort to ***photorec***.

---

