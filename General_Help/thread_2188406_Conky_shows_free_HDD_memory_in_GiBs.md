---
title: "Conky shows free HDD memory in GiBs"
date: 2013-11-17
forum: General Help
---

### Post by Vukatamayn on 2013-11-17
Hello!
How to edit Conky to shows free disk memory in GBs?
That's my code:

```

${font Kelly Slab :size=20}${color 98ff98}Heim:${alignr}${font Kelly Slab :size=20}${color 880206}${fs_free /home/tbk515}${color}${font}
${font Kelly Slab :size=20}${color 98ff98}515:${alignr}${font Kelly Slab :size=20}${color 880206}${fs_free /mnt}${color}${font}
${font Kelly Slab :size=20}${color 98ff98}TBK:${alignr}${font Kelly Slab :size=20}${color 880206}${fs_free /media/TBK}${color}${font}
${font Kelly Slab :size=20}${color 98ff98}tbk515:${alignr}${font Kelly Slab :size=20}${color 880206}${fs_free /media/tbk515}${color}${font}    
```

And that appears:

[IMG]http://s8.postimg.org/3q64ht4mt/asa.png[/IMG]

Question 2: Is it possible to insert space between numbers and letters? How?
Sorry, if the thread is in wrong place!
Sorry for my bad English!
Thanks!

---

### Post by Toz on 2013-11-17
Hello and welcome to the forums.

> How to edit Conky to shows free disk memory in GBs?
The results showing are in Gibibytes (based on 1024 bits per megabyte - [see here]("http://en.wikipedia.org/wiki/Binary_prefix") for explanation). You can shorten the "GiB" to just "G" by setting:
```
short_units yes
```

---

### Post by ajgreeny on 2013-11-17
> **Toz said:**
> Hello and welcome to the forums.


The results showing are in Gibibytes (based on 1024 bits per megabyte - [see here]("http://en.wikipedia.org/wiki/Binary_prefix") for explanation). You can shorten the "GiB" to just "G" by setting:
```
short_units yes
```But it will still be showing GiB in spite of the display, which I don't think is what the OP wants.

Perhaps I misunderstood the original reason for the question?

---

### Post by Vukatamayn on 2013-11-18
@Toz, I know the difference between GiB and GB, but your proposed code still shows free space on HDDs in GiB. Thanks however!

@ajgreeny, I want conky to calculate free disk space in GB, because a few weeks ago I bought 2 new external HDD!

Thanks, again!

---

### Post by stinkeye on 2013-11-18
Would df give you the output you want.

from man df
> -h, --human-readable
 print sizes in human readable format (e.g., 1K 234M 2G) 
-H, --si
 likewise, but use powers of 1000 not 1024

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **df [COLOR="#FF0000"]-H[/COLOR]**
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       186G   28G  149G  16% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            1.1G   13k  1.1G   1% /dev
tmpfs           1.1G  1.6M  1.1G   1% /tmp
tmpfs           210M  1.1M  209M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            1.1G  115k  1.1G   1% /run/shm
none            105M   41k  105M   1% /run/user
/dev/sdc7       289G  133G  141G  49% /media/Data
/dev/sdc2        53G  1.4G   49G   3% /media/glen/SaucyHome
/dev/sdc1        41G  5.2G   34G  14% /media/glen/SaucySys

[COLOR="#008000"]glen@Raring:~$[/COLOR] **df [COLOR="#FF0000"]-H[/COLOR] /dev/sdc2 | awk 'END{print $4}'**
49G

[COLOR="#008000"]glen@Raring:~$[/COLOR] **df [COLOR="#FF0000"]-h[/COLOR] /dev/sdc2 | awk 'END{print $4}'**
46G
```

eg for conky....
```
${execi 1800 df -H /dev/sdc2 | awk 'END{print $4}'}
```

---

### Post by Vukatamayn on 2013-11-19
> **stinkeye said:**
> 
eg for conky....
```
${execi 1800 df -H /dev/sdc2 | awk 'END{print $4}'}
```

Thanks a lot for code! Here's the result:

[IMG]http://s21.postimg.org/nb1yqiglz/zaz.png[/IMG]

Thread is solved!

---

