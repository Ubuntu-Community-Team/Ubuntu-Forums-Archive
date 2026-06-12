---
title: "MDADM Array won't start"
date: 2013-10-09
forum: General Help
---

### Post by Stu_Jessop on 2013-10-09
I have a 12.xx server that has been running for quite a while.  I recently powered it off for a few weeks and when it came back up it hung because the array wouldn't start.  I have the OS on a stand-alone disk and just use the array for media storage.  So, I have access to the OS after I exit the initramfs screen.  I am working remotely and have a non-technical person working the keyboard for me until I can get the OS to boot completely.  

Here is the some of the relevant information from the server:

4x2TB drives in a RAID5 array, ~6TB usable space
OS is installed on SDA
RAID is : SDB, SDC, SDD, SDE (SDE is apparently off-line at the moment, I'll troubleshoot that when I am in front of the box)

mdadm --assemble --scan return nothing
[INDENT]root@media-server:/etc/default# mdadm --assemble  --scan[/INDENT]
[INDENT]root@media-server:/etc/default# [/INDENT]

blkid shows that I clearly have array members installed
[INDENT]root@media-server:/etc/default# blkid[/INDENT]
[INDENT]/dev/sda1: UUID="d3a63f94-a32f-430d-839a-ebb2b2a26a39" TYPE="ext4" [/INDENT]
[INDENT]/dev/sda5: UUID="bf2421a7-3bc9-490e-a2a2-403465b85069" TYPE="swap" [/INDENT]
[INDENT]/dev/sdb1: UUID="4f624b29-9cd3-1bae-8d4d-b4003b4cc629" UUID_SUB="8d66afc7-fc47-e2a9-7ae4-75bd2f413884" LABEL="media-server:1" TYPE="linux_raid_member" [/INDENT]
[INDENT]/dev/sdc1: UUID="4f624b29-9cd3-1bae-8d4d-b4003b4cc629" UUID_SUB="9f1326b2-fd9a-5a56-51c8-6e55f6e620c7" LABEL="media-server:1" TYPE="linux_raid_member" [/INDENT]
[INDENT]/dev/sdd1: UUID="4f624b29-9cd3-1bae-8d4d-b4003b4cc629" UUID_SUB="697eeced-986c-e7ea-590a-5ba3e6c0db97" LABEL="media-server:1" TYPE="linux_raid_member" [/INDENT]
[INDENT]root@media-server:/etc/default# [/INDENT]

cat /proc/mdstat shows the array inactive.  Does the S indicate that mdadm thnks the drives are spares?
[INDENT]>root@media-server:/etc/default# cat /proc/mdstat[/INDENT]
[INDENT]>Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/INDENT]
[INDENT]>md127 : inactive sdc1[5](S) sdb1[4](S) sdd1[1](S)[/INDENT]
[INDENT]>      5860537432 blocks super 1.2[/INDENT]
[INDENT]       [/INDENT]
[INDENT]>unused devices: <none>[/INDENT]
[INDENT]>root@media-server:/etc/default# [/INDENT]

Any ideas on what I can do to get this thing to boot again?


thanks


stu...

---

### Post by SaturnusDJ on 2013-10-09
Stop all arrays containing the members of the one you want to assemble.
Then:
```

mdadm --assemble /dev/md0 --uuid=4f624b29-9cd3-1bae-8d4d-b4003b4cc629

```

If it doesn't want to, check if the 'Events' for the drives don't differ too much (mdadm --examine) and:
```

mdadm --assemble --force --run /dev/md0 --uuid=4f624b29-9cd3-1bae-8d4d-b4003b4cc629

```

---

### Post by Stu_Jessop on 2013-10-09
Thanks for the tips.  I tried that, no joy.

[INDENT]root@media-server:/var/log# mdadm --examine
mdadm: No devices to examine[/INDENT]

For some reason mdadm isn't seeing my drives at all.  I'm afraid to reboot it as I've lost my hands on-site and won't be able to get past the initramfs screen without them.  I guess I might be headed that way this weekend if I can't figure this out remotely.

Does the S in the /proc/mdstat indicate that mdadm thinks the drives are spares?

[INDENT]root@media-server:/var/log# cat /proc/mdstat[/INDENT]
[INDENT]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/INDENT]
[INDENT]md127 : inactive sdc1[5](S) sdb1[4](S) sdd1[1](S)[/INDENT]
[INDENT]      5860537432 blocks super 1.2[/INDENT]
[INDENT]       [/INDENT]
[INDENT]unused devices: <none>

[/INDENT]
thanks

stu...

---

### Post by SaturnusDJ on 2013-10-09
I had to explain better.
mdadm --examine is followed by an array member. :)
Like in your case:
```
mdadm --examine /dev/sd[b-d]1
```

---

### Post by Stu_Jessop on 2013-10-09
Ok, I have some inconsistency in what the individual drives think they are seeing.  One drive shows active, the others show clean.  More worrying is that they don't all have the same array state.  What could cause them get so out of whack like this?

[INDENT]root@media-server:/var/log# mdadm --examine /dev/sdb1[/INDENT]
[INDENT]/dev/sdb1:[/INDENT]
[INDENT]          Magic : a92b4efc[/INDENT]
[INDENT]        Version : 1.2[/INDENT]
[INDENT]    Feature Map : 0x0[/INDENT]
[INDENT]     Array UUID : 4f624b29:9cd31bae:8d4db400:3b4cc629[/INDENT]
[INDENT]           Name : media-server:1  (local to host media-server)[/INDENT]
[INDENT]  Creation Time : Tue Jun 11 12:35:37 2013[/INDENT]
[INDENT]     Raid Level : raid5[/INDENT]
[INDENT]   Raid Devices : 4[/INDENT]
[INDENT]
[/INDENT]
[INDENT] Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)[/INDENT]
[INDENT]     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)[/INDENT]
[INDENT]  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)[/INDENT]
[INDENT]    Data Offset : 2048 sectors[/INDENT]
[INDENT]   Super Offset : 8 sectors[/INDENT]
[INDENT]          State : clean[/INDENT]
[INDENT]    Device UUID : 8d66afc7:fc47e2a9:7ae475bd:2f413884[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    Update Time : Tue Oct  8 20:29:42 2013[/INDENT]
[INDENT]       Checksum : cf2b9437 - correct[/INDENT]
[INDENT]         Events : 36847[/INDENT]
[INDENT]
[/INDENT]
[INDENT]         Layout : left-symmetric[/INDENT]
[INDENT]     Chunk Size : 512K[/INDENT]
[INDENT]
[/INDENT]
[INDENT]   Device Role : Active device 3[/INDENT]
[INDENT]**   Array State : .A.A ('A' == active, '.' == missing)**[/INDENT]
[INDENT]root@media-server:/var/log# mdadm --examine /dev/sdc1[/INDENT]
[INDENT]/dev/sdc1:[/INDENT]
[INDENT]          Magic : a92b4efc[/INDENT]
[INDENT]        Version : 1.2[/INDENT]
[INDENT]    Feature Map : 0x0[/INDENT]
[INDENT]     Array UUID : 4f624b29:9cd31bae:8d4db400:3b4cc629[/INDENT]
[INDENT]           Name : media-server:1  (local to host media-server)[/INDENT]
[INDENT]  Creation Time : Tue Jun 11 12:35:37 2013[/INDENT]
[INDENT]     Raid Level : raid5[/INDENT]
[INDENT]   Raid Devices : 4[/INDENT]
[INDENT]
[/INDENT]
[INDENT] Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)[/INDENT]
[INDENT]     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)[/INDENT]
[INDENT]  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)[/INDENT]
[INDENT]    Data Offset : 2048 sectors[/INDENT]
[INDENT]   Super Offset : 8 sectors[/INDENT]
[INDENT]          State : active[/INDENT]
[INDENT]    Device UUID : 9f1326b2:fd9a5a56:51c86e55:f6e620c7[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    Update Time : Tue Oct  8 15:16:56 2013[/INDENT]
[INDENT]       Checksum : 40fdd0ba - correct[/INDENT]
[INDENT]         Events : 36031[/INDENT]
[INDENT]
[/INDENT]
[INDENT]         Layout : left-symmetric[/INDENT]
[INDENT]     Chunk Size : 512K[/INDENT]
[INDENT]
[/INDENT]
[INDENT]   Device Role : Active device 0[/INDENT]
[INDENT]**   Array State : AA.A ('A' == active, '.' == missing)**[/INDENT]
[INDENT]root@media-server:/var/log# mdadm --examine /dev/sddd1[/INDENT]
[INDENT]mdadm: cannot open /dev/sddd1: No such file or directory[/INDENT]
[INDENT]root@media-server:/var/log# mdadm --examine /dev/sdd1[/INDENT]
[INDENT]/dev/sdd1:[/INDENT]
[INDENT]          Magic : a92b4efc[/INDENT]
[INDENT]        Version : 1.2[/INDENT]
[INDENT]    Feature Map : 0x0[/INDENT]
[INDENT]     Array UUID : 4f624b29:9cd31bae:8d4db400:3b4cc629[/INDENT]
[INDENT]           Name : media-server:1  (local to host media-server)[/INDENT]
[INDENT]  Creation Time : Tue Jun 11 12:35:37 2013[/INDENT]
[INDENT]     Raid Level : raid5[/INDENT]
[INDENT]   Raid Devices : 4[/INDENT]
[INDENT]
[/INDENT]
[INDENT] Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)[/INDENT]
[INDENT]     Array Size : 11721071616 (5589.04 GiB 6001.19 GB)[/INDENT]
[INDENT]  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)[/INDENT]
[INDENT]    Data Offset : 2048 sectors[/INDENT]
[INDENT]   Super Offset : 8 sectors[/INDENT]
[INDENT]          State : clean[/INDENT]
[INDENT]    Device UUID : 697eeced:986ce7ea:590a5ba3:e6c0db97[/INDENT]
[INDENT]
[/INDENT]
[INDENT]    Update Time : Tue Oct  8 20:29:42 2013[/INDENT]
[INDENT]       Checksum : 2ff67593 - correct[/INDENT]
[INDENT]         Events : 36847[/INDENT]
[INDENT]
[/INDENT]
[INDENT]         Layout : left-symmetric[/INDENT]
[INDENT]     Chunk Size : 512K[/INDENT]
[INDENT]
[/INDENT]
[INDENT]   Device Role : Active device 1[/INDENT]
[INDENT]**   Array State : .A.A ('A' == active, '.' == missing)**[/INDENT]
[INDENT]root@media-server:/var/log#[/INDENT]

---

### Post by SaturnusDJ on 2013-10-09
Ok, indeed /dev/sde is missing.

Read [https://raid.wiki.kernel.org/index.php/RAID_Recovery#Trying_to_assemble_using_--force](https://raid.wiki.kernel.org/index.php/RAID_Recovery#Trying_to_assemble_using_--force)

/dev/sdc1 is outdated.
I suggest to wait until you're able to find out what's up with /dev/sde. Best case it's ok and has an event count of 36847. Then you can assemble degraded, and add /dev/sdc1 back.
You better make a back-up before doing that however, because if a drive fails during the resync things become more difficult.

---

### Post by Stu_Jessop on 2013-10-09
Thanks.  I'll leave it as-is for now until I can get eyes on the problem.

---

### Post by Stu_Jessop on 2013-10-10
I powered everything down and when it recovered, the system saw all four drives.  I then forced the assemble with the uuid specified and it started with 3/4 drives.  I manually added the fourth drive and it is rebuilding the sync data now.  Thanks saturnusdj, you taught me a ton and saved me even more work!


stu...

---

