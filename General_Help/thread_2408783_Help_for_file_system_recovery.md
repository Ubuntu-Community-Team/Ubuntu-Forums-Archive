---
title: "Help for file system recovery"
date: 2018-12-23
forum: General Help
---

### Post by GirishSharma on 2018-12-23
Hello,


I am running Ubuntu 18.04 LTS 64 bit PC with 2 HDDs. One is 240 GB SSD and 1 is 1 TB HDD. Ubuntu is in SSD and for storage and backup
I usages 1 TB HDD which have two ext4 partitions. All was running fine, but I don't know my some data got lost or messed up in 1 TB HDD. Here is some more info for help please :

```

girish@gk:~$ sudo fdisk -l
Disk /dev/loop0: 88.2 MiB, 92483584 bytes, 180632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 89.5 MiB, 93818880 bytes, 183240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 128 KiB, 131072 bytes, 256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 2.7 MiB, 2797568 bytes, 5464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 200 KiB, 204800 bytes, 400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 89.5 MiB, 93835264 bytes, 183272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5475bcda


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 435589119 435587072 207.7G 83 Linux
/dev/sda2       435591166 468860927  33269762  15.9G  5 Extended
/dev/sda5       435591168 468860927  33269760  15.9G 82 Linux swap / Solaris




Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2052474d


Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1          6579571 1924427647 1917848077 914.5G 70 DiskSecure Multi-Boot
/dev/sdb2       1953251627 3771827541 1818575915 867.2G 43 unknown
/dev/sdb3        225735265  225735274         10     5K 72 unknown
/dev/sdb4       2642411520 2642463409      51890  25.3M  0 Empty


Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.

```


When I Says :

```

girish@gk:~$ sudo fsck -nf /dev/sdb1
[sudo] password for girish: 
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Pass 1: Checking inodes, blocks, and sizes
e2fsck: aborted
girish@gk:~$ sudo fsck -nf /dev/sdb2
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb2: 820237/22691840 files (0.1% non-contiguous), 33226842/90737837 blocks

```


and here is how lost+found looks like :

```

girish@gk:/media/girish/60975232-440b-4723-872c-8242ebf49b39$ sudo su
root@gk:/media/girish/60975232-440b-4723-872c-8242ebf49b39# cd lost+found/
root@gk:/media/girish/60975232-440b-4723-872c-8242ebf49b39/lost+found# ls -lort
ls: cannot access '#27001659': Structure needs cleaning
ls: cannot access '#27001933': Structure needs cleaning
ls: cannot access '#27002760': Structure needs cleaning
ls: cannot access '#27002325': Structure needs cleaning
ls: cannot access '#27002496': Structure needs cleaning
ls: cannot access '#27002629': Structure needs cleaning
ls: cannot access '#27002167': Structure needs cleaning
total 1857156
s--xr-Srwt 1 1901085376         0 Mar 31  1902 '#23200237'
p--xr-sr-x 1 2239788099         0 Mar 31  1902 '#23200055'
sr--r-x-wT 1 2239802641         0 Mar 31  1902 '#23199965'
d--------T 2    1839118      4096 Aug 19  1903 '#27002925'
sr---ws-w- 1 3291206745         0 Mar 17  1904 '#27394347'
c--s---rwT 1 3359860944  172,  64 Aug 21  1904 '#23070396'
srw---x--t 1      63976         0 Nov 20  1906 '#27001503'
srwS--s--t 1 3959392588         0 Nov 24  1906 '#27001489'
p-w---s--x 1   80627715         0 Dec 13  1907 '#27001746'
drw---s-wt 2 1210006312      4096 Dec 13  1907 '#27001214'
d--------T 2 1495797774      4096 May 31  1908 '#27002665'
c--xrwxrwx 1 3684434928   82, 138 Sep 29  1911 '#27394606'
brwxr-xr-t 1 3455261248  116, 131 Jul  2  1914 '#23070659'
srwS---rwt 1 1992117229         0 Jul  8  1914 '#22938547'
c--x-wx-w- 1 3403283018  101,   6 Nov 27  1918 '#27394146'
d--s-w---- 2 1187472873      4096 May 13  1919 '#27000957'
b-wx--S-wt 1 1672470901  222, 222 Nov  5  1922 '#23069071'
s--x-ws-w- 1  596367570         0 Dec  5  1926 '#27394203'
cr-Srwx--t 1 3614516623    4,  41 Apr  6  1928 '#23070622'
.....

```


To solve the issue I have followed [https://superuser.com/questions/1248832/cant-run-fsck-e2fsck-aborted](https://superuser.com/questions/1248832/cant-run-fsck-e2fsck-aborted) too :

```

girish@gk:~/e2fsprogs-1.43.1/e2fsck$ sudo ./e2fsck /dev/sdb2
[sudo] password for girish: 
e2fsck 1.43.1 (08-Jun-2016)
/dev/sdb2: clean, 820237/22691840 files, 33226842/90737837 blocks
girish@gk:~/e2fsprogs-1.43.1/e2fsck$ sudo ./e2fsck /dev/sdb1
e2fsck 1.43.1 (08-Jun-2016)
/dev/sdb1: clean, 148337/53190656 files, 28204947/212758116 blocks
girish@gk:~/e2fsprogs-1.43.1/e2fsck$ 

```


But, I am not able to get back the data from lost+found, and resolve Structure needs cleaning and "Partition 1 does not start on physical sector boundary." from fdisk command.


I don't know how do I resolve it. Kindly help me.  I will try my best to answer all your question(s) for required info.


Thanks and Regards.
Girish Sharma

---

