---
title: "Does Ubuntu respect presence of SSDs?"
date: 2019-07-23
forum: General Help
---

### Post by Krischu on 2019-07-23
SSDs require special treatment regarding writing to the disk. Does Ubuntu respect the presence of SSDs as the system disk and behave correspondingly?

---

### Post by sevendogs1337 on 2019-07-23
What are you referring to by "special treatment"? Modern SSDs are very robust and you do not have to do anything special to them to use them in any OS. By default, TRIM is enabled in Ubuntu via systemd, for ext4 anyway, can't speak to any other file systems. That is the only type of maintenance that is required. The ONLY other thing is to not use "discard" in /etc/fstab and instead use the "noatime" option. Neither one of those options will kill an SSD though. I have been  using and beating the heck out of my Samsung 850 Pro SSDs for over 3 years and tey are going strong.

---

### Post by QIII on 2019-07-23
It seems as though you may be under some misapprehension that SSDs are some newly introduced bleeding-edge technology that Linux developers have never seen because they are still tinkering with 5 1/4" floppies.

I have been running SSDs for years and my current primary machine has nothing but NVMe SSDs.

The bulk of the "special treatment" in writing to SSDs is handled by the device firmware, which often does not treat commands that worked with mechanical drives in the same manner.  Linux uses SSD specific commands such as TRIM just fine.

Believe it or not, research into what became the SSD started in the 1950s.  One of the earliest commercially available "SSD"s (sometimes called "RAMDisks") came out in about 1978 for IBM machines.  At the time, Windows as you know it did not exist.  Those devices were utilized on machines running UNIX.  Those devices, however, cost hundreds of thousands of dollars.

You may not have seen SSDs until the last few years because the price of such devices did not come down far enough to hit the consumer market until then.

---

### Post by cruzer001 on 2019-07-23
I also waited for SSD prices to drop and have now been using them for a couple of years.  Been using the cheap oddball ones and have not yet to hit on one that linux will not run.

---

### Post by freemedia2018 on 2019-07-23
Of relevance is that SSD is gradually moving away from AHCI towards other modes like Intel IRRT.

I'm not certain that IRRT is the specific mode I'm thinking of; I know that AHCI is not newer.

I got my first SSD years ago, ran Refracta on it, gave it away in the netbook (yes, low-powered thing) I had installed it in.

---

### Post by Bashing-om on 2019-07-23
Krischu; Hello:

> **Krischu said:**
> SSDs require special treatment regarding writing to the disk. Does Ubuntu respect the presence of SSDs as the system disk and behave correspondingly?

My current setup:
```

sysop@x1804mini:~$ sudo lshw -C Disk -short
[sudo] password for sysop: 
H/W path         Device      Class       Description
====================================================
/0/b/0.0.0       /dev/cdrom  disk        DVD-ROM SD-M1502
/0/b/0.1.0       /dev/cdrw   disk        DVD-RAM GH22NP20
/0/10/0.0.0      /dev/sda    disk        120GB PNY CS900 120GB
/0/11/0.0.0      /dev/sdb    disk        250GB Samsung SSD 850
sysop@x1804mini:~$ 

```
Nary a problem :)

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by sevendogs1337 on 2019-07-23
Wanted to post some smartctl readings just for giggles. The drive below is my Samsung 850 EVO 256GB and is a little over 3 years old. I have done countless Linux and FreeBSD installs on it and formatted it so many times it's ridiculous. The drive is very healthy. Wear leveling count starts at 100 and goes down as the drive ages. You'll notice my wear leveling count is at 98.

```

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       5631
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       1438
177 Wear_Leveling_Count     0x0013   098   098   000    Pre-fail  Always       -       25
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   074   062   000    Old_age   Always       -       26
195 ECC_Error_Rate          0x001a   200   200   000    Old_age   Always       -       0
199 CRC_Error_Count         0x003e   100   100   000    Old_age   Always       -       0
235 POR_Recovery_Count      0x0012   099   099   000    Old_age   Always       -       269
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       15341709401

```

---

### Post by kpatz on 2019-07-23
Wear leveling count is more a function of how much data is written as opposed to number of times the drive has been formatted/reused.

Formatting the drive or partition (which in most cases only writes filesystem metadata), filling it with 200GB, then formatting again and filling with 200GB again will cause more wear than filling it with 20GB each time.  Wear leveling ensures that the memory cells are evenly used over time as much as possible, and in fact, if you're reformatting and reusing the drive, it can even out the wear even better than if you have a ton of static data on there.

Doing a secure wipe each time would bump up the wear level as well.

---

### Post by sevendogs1337 on 2019-07-23
Thanks for the info, good to know!

---

