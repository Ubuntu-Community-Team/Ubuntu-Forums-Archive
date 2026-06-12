---
title: "Troubleshooting help for newer user"
date: 2013-09-09
forum: General Help
---

### Post by Carey_Reynolds on 2013-09-09
Hello all, first post here, but I have read several forum posts on my issue. I'm newer to linux, but can do the basics and follow commands. 

I've got an issue with my ubuntu system crashing, and the displayed graphics skew diagonally. I am unable to send any commands at that point, and must hard reset via the power switch on the case. My system seems to work fine until I start transferring files from my mdadm raid5 array. I believe the issue has something to do with either the raid5 array, samba sharing (file transfers/viewing on this machine initiates the crash), or some hardware issue. 

I previously had issues when the array went to resync. The process was extremely slow, and would always cause a hard reset crash within a few minutes of booting. I got around this by booting a linux rescue cd, which could resync the array without crashes, but took several days. I believe I have solved the resync issue with:

mdadm --grow --bitmap=internal /dev/md0

But I have not since had a resync to test and see. Here is my current /proc/mdstat:

Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdh[5] sdi[2] sdg[0] sdf[7] sdd[4] sdc[1] sdb[6]
      11721077760 blocks super 1.2 level 5, 512k chunk, algorithm 2 [7/7] [UUUUUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk


unused devices: <none>

I have also attached the saved dmesg file from /var/log/dmesg

I installed crashdump, but it doesn't seem to be working when a crash occurs as there is no crash log after a reboot. If there are any other commands/logs that anyone wants to see please just respond and I can produce them. I appreciate any hints on commands/logs I should check as well. Thanks for any help!

---

### Post by Carey_Reynolds on 2013-09-10
Tried watching dmesg with: watch "dmesg | tail -20" while transferring files, and was not able to see any error messages before the inevitable crash. Only items that displayed were network transfer log entries. 

I then tried to transfer files to a usb hdd to figure out if the issue was network related. The result was the same, crashing after around 10 minutes of transferring. I'm thinking this has to be related to the raid 5 array, but I can't get any evidence of why in the dmesg log. Are there any other logs I can check? Thanks,[COLOR=#EFEFEF][FONT=Verdana][B]
[/B][/FONT][/COLOR]

---

