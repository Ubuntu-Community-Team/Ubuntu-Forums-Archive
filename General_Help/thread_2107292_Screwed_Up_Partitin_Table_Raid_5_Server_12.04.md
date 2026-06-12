---
title: "Screwed Up Partitin Table Raid 5 Server 12.04"
date: 2013-01-21
forum: General Help
---

### Post by Image0fman on 2013-01-21
Hello it seems that I am having an issue with my partition table according to the ouput from 'fdisk -l' listed below (invalid partition table). I've googled around but cannot find anything wrong with my current setup that would cause an error like that. I recently built a raid 5 array with 3 1.5TB physical disks. When I created the array I tried creating it as /dev/md/myraid but it defaulted to /dev/md127 for some reason. I also posted the output of mdadm --examine --scan and the contents of mdadm.conf. I can successfully mount the raid but its /dev/md127 not /dev/md/myraid.. maybe someone here has some experience with this stuff, I am kind of new too soft raid on nix. 

Thank You


fdisk -l 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030b0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    43812863    21905408   83  Linux
/dev/sda2        43814910   976771071   466478081    5  Extended
/dev/sda5       973647872   976771071     1561600   82  Linux swap / Solaris
/dev/sda6       827600896   973647871    73023488   83  Linux
/dev/sda7       710762496   827598847    58418176   83  Linux
/dev/sda8       617293824   710760447    46733312   83  Linux
/dev/sda9        43814912   617291775   286738432   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
30 heads, 63 sectors/track, 1550411 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055bc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930277167  1465137560   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
30 heads, 63 sectors/track, 1550411 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008677f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2930277167  1465137560   83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
30 heads, 63 sectors/track, 1550411 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4977

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  2930277167  1465137560   83  Linux

Disk /dev/md127: 3000.3 GB, 3000332451840 bytes
2 heads, 4 sectors/track, 732503040 cylinders, total 5860024320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

```mdadm --examine --scan 
```
ARRAY /dev/md/myraid metadata=1.2 UUID=da31423e:6e5727a2:4c77b0fd:db72a999 name=servername:myraid
```mdadm.conf
```
ARRAY /dev/md/myraid metadata=1.2 name=servername:myraid UUID=da31423e:6e5727a2:4c77b0fd:db72a999

```mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid5 sdb1[0] sdc1[1] sdd1[3]
      2930012160 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

```

---

### Post by Image0fman on 2013-01-22
Bump

---

### Post by tgalati4 on 2013-01-22
Fdisk will only enumerate real hardware devices.  /dev/md127 is a virtual device, created by mdadm that consists of your RAID drives.  I don't see a problem.  As to why mdadm didn't use your label is a mystery.  What was the exact command that you used?

```
history
```

---

### Post by Image0fman on 2013-01-25
> **tgalati4 said:**
> Fdisk will only enumerate real hardware devices.  /dev/md127 is a virtual device, created by mdadm that consists of your RAID drives.  I don't see a problem.  As to why mdadm didn't use your label is a mystery.  What was the exact command that you used?

```
history
```


Hello! Terribly Sorry for the late response! I appreciate your reply!

Here is the command I used to create the arrary

```
mdadm -C /dev/md/myraid -v --raid-devices=3 --level=5 /dev/sdb1 /dev/sdc1 /dev/sdd1

```

---

### Post by steeldriver on 2013-01-25
I *think* the answer is that the arrays get assembled at boot time *before* the mdadm.conf file is available - so you need to write the config into initramfs as well using

```
sudo update-initramfs -u
```

See [http://askubuntu.com/questions/209702/why-is-my-raid-dev-md1-showing-up-as-dev-md126-is-mdadm-conf-being-ignored](http://askubuntu.com/questions/209702/why-is-my-raid-dev-md1-showing-up-as-dev-md126-is-mdadm-conf-being-ignored)

---

