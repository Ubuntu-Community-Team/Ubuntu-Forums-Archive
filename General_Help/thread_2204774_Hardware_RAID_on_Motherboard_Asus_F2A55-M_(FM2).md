---
title: "Hardware RAID on Motherboard Asus F2A55-M (FM2)"
date: 2014-02-10
forum: General Help
---

### Post by marcolino7 on 2014-02-10
[COLOR=#000000]Hi,
I'm pretty new to Ubuntu. Tomorrow I'll receive my motherboard [/COLOR][COLOR=#000000]Asus F2A55-M (FM2). I need to use RAID1 disk configuration and I would like to perfom raid operation with motherboard controller.
My question id if it's possible to check the RAID status from Ubuntu. This is very important for me, and this help me to choose between Ubuntu and Windows.
Thanks

Marcolino[/COLOR]

---

### Post by IPvFletch on 2014-02-10
I use SIstatus for this. It's a program I got from my HW ppl (mine is a SuperMicro RAID controller). No idea if it will work, but if you want to try, here is the binary.. It runs on Ubuntu just fine but you'll need to have the ia32-libs (32-bit compatibility libraries) installed if you're running a 64-but Linux kernel... I don't have the source code, sorry. 

[ATTACH]250253[/ATTACH]



root@lnx6500:~# ./SIstatus -C
Captive RAID1 verify starting...
Starting consistency check on Drive0...
RAID status: Verify completed Drive0
Starting consistency check on Drive1...
RAID status: Verify completed Drive1
RAID1 volume verify completed.




root@lnx6500:~# ./SIstatus -i


Getting RAID information
======================================
SI Module device path: /dev/sda
Firmware Version: 11546
SI module s/n: 12345678
SI Chip ID: 127
SI module policy:       SAFE
Drive0 model: WDC WD800JD-00LSA5
Drive1 model: WDC WD800JD-00LSA5
Drive0 s/n:      WD-WMAM9XY70927
Drive1 s/n:      WD-WMAM9XZ55076
Drive0 capacity (GB): 74
Drive1 capacity (GB): 74




root@lnx6500:~# ./SIstatus -s


Getting RAID Status
======================================
Drive0: On-line
Drive1: On-line
RAID status: Healthy












======================================
FOR NEW DRIVES OR TO RE-INIT DRIVES
======================================


[0249032010200003:~]# SIstatus -r
Initializing and resetting RAID Array...
RAID Array reset/initialize sent. Please perform a hard reset by cycling power.
[0249032010200003:~]#



--

Also look for dosdvr.exe - you can use this to init HW RAIDs (for new disks, to stop the beeping). I used it and it worked for me when I put in 2 new 500GB disks!

---

