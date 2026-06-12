---
title: "Speed of software RAID 0 with 4 SSD drives is strange"
date: 2018-09-18
forum: General Help
---

### Post by maksimikhalchuk on 2018-09-18
[SIZE=4]**[B]Situation:**[/B][/SIZE]

[COLOR=#242729][FONT=Arial]I have a server working on **Ubuntu Server 16.04**. I created software **RAID 0** array that contains 4 **SSD** drives.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When I checked the speed of the RAID array on my server I was confused. I was supposed to see that read speed is about **1200 MB/s** (300 MB/s * 4) and write speed is about **1100 MB/s** (300 MB/s * 4 - %). But, instead I saw only **860 MB/s** for read speed and **80 MB/s** for write speed.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I decided to check if this issue is connected to hardware. So, I created RAID 0 that contains 4 SSD drives, but now on my **desktop**. Every single hardware component is different there + it's **Ubuntu Desktop 16.04** (AMD-64).
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When I checked the speed of the RAID array on my desktop I saw only **696 MB/s** for read speed and **178 MB/s** for write speed. So, now I'm sure that it's **Ubuntu 16.04** problem or **SSD drive **problem.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What are the causes of this issue and how to solve it?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks for help
[/FONT][/COLOR]
[SIZE=4]**[B]RAID configuration:**[/B][/SIZE]


[LIST=1]
[*][FONT=inherit]sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=4 /dev/sdc /dev/sdd /dev/sde /dev/sdf[/FONT]
[*][FONT=inherit]sudo mkfs.ntfs -F /dev/md0[/FONT]
[*][FONT=inherit]sudo mkdir -p /mnt/md0[/FONT]
[*][FONT=inherit]sudo mount /dev/md0 /mnt/md0[/FONT]
[*][FONT=inherit]sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf[/FONT]
[/LIST]
[B][B]
[SIZE=4]Specifications:[/SIZE][/B][/B]

[SIZE=3][B][B]Server:
[/B][/B][/SIZE]
[LIST]
[*]**Operating system:**[COLOR=#242729][FONT=Arial] Ubuntu Server 16.04 (AMD-64) [/FONT][/COLOR]
[*]**SATA Interface:**[COLOR=#242729][FONT=Arial] II[/FONT][/COLOR]
[/LIST]

[SIZE=3]**[B]Disks:**[/B][/SIZE][COLOR=#242729][FONT=Arial]

[LIST]
[*]**Type:** SSD
[*]**Interface:** SATA III + SATA II
[*]**Capacity:** 480 GB
[*]**Controller:** Phison S11
[*]**Read Speed:** 560 MB/s
[*]**Write Speed:** 540 MB/s
[/LIST]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]• Full specifications you can get [there]("https://www.newegg.com/Product/Product.aspx?reviews=all&Item=N82E16820225111") (tab *specifications*)
[/FONT][/COLOR]
[SIZE=3]**[B]RAID:**[/B][/SIZE][COLOR=#242729][FONT=Arial]

[LIST]
[*]**Level:** 0
[*]**Devices:** 4
[*]**File system:** NTFS
[*]**Read Speed:** 860 MB/s
[*]**Write Speed:** 80 MB/s
[/LIST]

• NTFS file system is used cause my SSD drives don't support Linux file systems
[/FONT][/COLOR]

---

### Post by TheFu on 2018-09-18
NTFS is the problem.  This is well-known due to a limit of the cache used.  When you mount it, use the big_writes option.  From the mount manpage:
```

       big_writes
              This option prevents fuse from splitting write buffers  into  4K
              chunks,  enabling  big  write buffers to be transferred from the
              application in a single step (up to some system limit, generally
              128K bytes).
```

Or use a Linux file system.  I've never heard of any storage that didn't support Linux unless the vendor refused to work with the Linux driver team.  Best to avoid those vendors.  Often, even without the vendor's help, 1-2 yrs later it will work assuming someone provides the linux developer with some hardware.

---

