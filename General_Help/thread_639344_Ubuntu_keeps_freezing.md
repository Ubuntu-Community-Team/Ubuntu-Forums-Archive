---
title: "Ubuntu keeps freezing"
date: 2007-12-13
forum: General Help
---

### Post by Robken on 2007-12-13
Hi guys, 

I installed ubuntu about 2 weeks ago, and I love it. But I got 1 annoying problem: about every 5 minutes ubuntu freezes for about 15-30 seconds. It's completely random, and it's very annoying, especially when I'm watching a movie. I did a search but didn't find any solution. So here are my speccs:

Acer Aspire 9410
[http://www.walmart.com/catalog/product.do?product_id=5969098#Specifications](http://www.walmart.com/catalog/product.do?product_id=5969098#Specifications)

Someone suggested I posted my log after one of those freezes, so here's the sudo tail /var/log/syslog output:

Dec 10 14:22:47 xxx-laptop kernel: [ 728.276000] ata1.01: configured for UDMA/33
Dec 10 14:22:47 xxx-laptop kernel: [ 728.276000] ata1: EH complete
Dec 10 14:22:47 xxx-laptop kernel: [ 728.292000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 10 14:22:47 xxx-laptop kernel: [ 728.300000] sd 0:0:0:0: [sda] Write Protect is off
Dec 10 14:22:47 xxx-laptop kernel: [ 728.300000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 10 14:22:47 xxx-laptop kernel: [ 728.400000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 10 14:22:47 xxx-laptop kernel: [ 728.460000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 10 14:22:47 xxx-laptop kernel: [ 728.476000] sd 0:0:0:0: [sda] Write Protect is off
Dec 10 14:22:47 xxx-laptop kernel: [ 728.476000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 10 14:22:47 xxx-laptop kernel: [ 728.508000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by Robken on 2007-12-14
Anyone? Seems quite a few people have this problem, but haven't found a solution yet.

---

### Post by FakeOutdoorsman on 2007-12-14
Sounds like there's a problem with the hard drive. Use a Live CD and run:
```
sudo fsck /dev/sda1
```

It will check for errors on the sda1 partition where Ubuntu should be installed.  You can list all of the partitions with:
```
sudo fdisk -l
```

---

### Post by xeth_delta on 2007-12-14
Can you check the CPU utilization when the system freezes?

---

### Post by FakeOutdoorsman on 2007-12-14
xeth_delta has a good idea.  Open a terminal and use the **top** command to see if anything is being a resource hog.  top will sort tasks by CPU usage.

---

### Post by Robken on 2007-12-15
Didn't have time to check all my hard disks with live cd yet, but I can tell that when it freezes, my CPU usage jumps to 100%.

---

### Post by xeth_delta on 2007-12-15
> **Robken said:**
> Didn't have time to check all my hard disks with live cd yet, but I can tell that when it freezes, my CPU usage jumps to 100%.

Please, use top to see what program is using that much CPU. Go to a terminal and run it from there.

---

### Post by gymmeh on 2008-01-31
I have an acer asper 5601 and have the exact same problem. 

My computer freezes completely randomly for 10-15 second about 5 to 10 times in 6 hours.

I have not been able to check the cpu usage while it freezes, is there any way to log it???

---

### Post by gymmeh on 2008-01-31
Fake, when you do that how will you know there is a hard drive problem??
what can you do about it if there is??

---

### Post by gymmeh on 2008-02-01
SO i booted from the live CD and all sorts of crap warnings and errors poped up.

this is what I got from it
/etc/X11/xorg.conf

parse error on line 93 of section monitor the HorizSync keyword must be followed by a list of numbers or ranges

ww = warning 

ww xf86close console: KDSET MODE failed: Bad file descriptor
ww xf86close console: VT_GETMODE failed: Bad file descriptor
ww xf86close console: VT_GETSTATE failed: Bad file descriptor


SO what do I do now???

---

### Post by Crafty Kisses on 2008-02-01
> **Robken said:**
> Hi guys, 

I installed ubuntu about 2 weeks ago, and I love it. But I got 1 annoying problem: about every 5 minutes ubuntu freezes for about 15-30 seconds. It's completely random, and it's very annoying, especially when I'm watching a movie. I did a search but didn't find any solution. So here are my speccs:

Acer Aspire 9410
[http://www.walmart.com/catalog/product.do?product_id=5969098#Specifications](http://www.walmart.com/catalog/product.do?product_id=5969098#Specifications)

Someone suggested I posted my log after one of those freezes, so here's the sudo tail /var/log/syslog output:

Dec 10 14:22:47 xxx-laptop kernel: [ 728.276000] ata1.01: configured for UDMA/33
Dec 10 14:22:47 xxx-laptop kernel: [ 728.276000] ata1: EH complete
Dec 10 14:22:47 xxx-laptop kernel: [ 728.292000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 10 14:22:47 xxx-laptop kernel: [ 728.300000] sd 0:0:0:0: [sda] Write Protect is off
Dec 10 14:22:47 xxx-laptop kernel: [ 728.300000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 10 14:22:47 xxx-laptop kernel: [ 728.400000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 10 14:22:47 xxx-laptop kernel: [ 728.460000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Dec 10 14:22:47 xxx-laptop kernel: [ 728.476000] sd 0:0:0:0: [sda] Write Protect is off
Dec 10 14:22:47 xxx-laptop kernel: [ 728.476000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 10 14:22:47 xxx-laptop kernel: [ 728.508000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Possibly a drive issue, post the following output: ```
top
```

---

### Post by LiNuXxToOthEMaX on 2008-02-01
> **Codename said:**
> Possibly a drive issue, post the following output: ```
top
```

Thanks Codename i was looking for a terminal thing to look at my resources

---

