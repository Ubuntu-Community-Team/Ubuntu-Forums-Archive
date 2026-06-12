---
title: "ext4 resized partion shows 0 bytes free instead of real capacity - screenshots"
date: 2014-06-13
forum: General Help
---

### Post by sp3cktator on 2014-06-13
Hi, 

I've run into this problem after resizing a partition of my WD green 1,5 TB HDD. The disk had two partitions, one with wind0ze (sdc1), one large partition for storage (1,3TB) and some unallocated space. I resized the storage patition in order to gain some space for ubuntu new installation. After gparted was finished i've come to realize that my storage partition ( sdc2) has 0 bytes free. I've tried df -h but nothing. Gparted thought returns the correct free capacity. Tried with fsck /dev/sdc2 and it returned that my partition seems to be ok. The problem is that i can't copy anything to that partition anymore. :(
see screenshots below.

[ATTACH=CONFIG]253924[/ATTACH][ATTACH=CONFIG]253925[/ATTACH]


How can i fix my partition?

---

### Post by sp3cktator on 2014-07-21
anyone?

---

### Post by steeldriver on 2014-07-21
Remember that the default ext4 reserves 5% of the total blocks so 'unused' does not necessarily correspond to 'available' - what do

```

df -h

df -i

```
(from a terminal) say?

---

### Post by sp3cktator on 2014-07-21
Thanks for noticing my post. (Edit: I wasn't ironic. I meant it.)
5% of 1,22T is 6.1GBytes  and not 54GBytes ;)

df -h :
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3              48G   45G  1,4G  98% /
none                  4,0K     0  4,0K   0% /sys/fs/cgroup
udev                  2,9G  4,0K  2,9G   1% /dev
tmpfs                 597M  1,3M  596M   1% /run
none                  5,0M     0  5,0M   0% /run/lock
none                  3,0G  1,5M  3,0G   1% /run/shm
none                  100M   40K  100M   1% /run/user
/home/kolpo/.Private   48G   45G  1,4G  98% /home/kolpo
---- >/dev/sdb2             1,3T  1,2T     0 100% /media/kolpo/terras
/dev/sda1              70G   50G   17G  75% /media/kolpo/4c678eac-e72f-4128-aa28-14fa66625643
/dev/sdb1              84G   76G  7,3G  92% /media/kolpo/EC72F00072EFCE00
/dev/sdc1             466G  146G  321G  32% /media/kolpo/Warlock
```

df -i :
```
Filesystem              Inodes  IUsed     IFree IUse% Mounted on
/dev/sdb3              3203072 421369   2781703   14% /
none                    763908     11    763897    1% /sys/fs/cgroup
udev                    751805    552    751253    1% /dev
tmpfs                   763908    584    763324    1% /run
none                    763908      8    763900    1% /run/lock
none                    763908     13    763895    1% /run/shm
none                    763908     28    763880    1% /run/user
/home/kolpo/.Private   3203072 421369   2781703   14% /home/kolpo
---> /dev/sdb2             81829888 514218  81315670    1% /media/kolpo/terras
/dev/sda1              4644864 599920   4044944   13% /media/kolpo/4c678eac-e72f-4128-aa28-14fa66625643
```

---

### Post by oldfred on 2014-07-21
I had not noticed that gparted uses GiB not GB, that could be your difference?

       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space for superuser.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)

---

