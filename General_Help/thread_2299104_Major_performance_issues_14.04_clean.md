---
title: "Major performance issues 14.04 clean"
date: 2015-10-15
forum: General Help
---

### Post by Lewis_Jessett on 2015-10-15
Hi I have just bought a lenovo thinkpad E550, and installed Ubuntu 14.04 onto it but I am running into major performance issues. Like 8 + seconds to launch any application from startup, Firefox runs incredibly slow it won't run a video smoothly. The hardware is certified to work with Ubuntu (my exact spec)

[http://www.ubuntu.com/certification/hardware/201411-16167/](http://www.ubuntu.com/certification/hardware/201411-16167/)

I have tried changing between integrated Intel graphics and the amd card. 

Changing CPU setting in BIOS.

I have done all updates to drivers and tried changing graphics drivers.

Installed preload and prelink

The laptop has a broad well i7, 8gb of ram I don't think it should be as slow as it is any help would be much appreciated.

Thanks
Lewis

---

### Post by mc4man on 2015-10-15
Don't have any amd video laptops so only a query for info that could be useful to others.
Open up System Settings > Details
(- click on the gear icon in upper right corner of panel, System Settings... in in the drop down or open a terminal (ctrl+alt+t) and go 
```
unity-control-center info
```
It will tell you what graphics you are currently using, LLVMpipe ... would be quite slow & not what you want. Otherwise post whether using amd or intel

---

### Post by nknwn on 2015-10-15
There is an application named SystemTesting. Search in Dash. You might want to take a look at that and carry out some of the tests on Graphics, Memory and HDD. See if it any problems becomes apparent. This laptop here has 8GB Memory and just for comparison I clicked on Libre office writer and it took about 6 seconds to present the GUI from cold. Thereafter it took less than a second. However I'm running Ubuntu from an external drive so I'd expect it to be faster if I swapped out the internal HDD.

---

### Post by Lewis_Jessett on 2015-10-16
Memory 7.5gb
Processor Intel® Core&#8482; i7-5500U CPU @ 2.40GHz × 4 
Graphics Intel® HD Graphics 5500 (Broadwell GT2) 
OS Type 64bit

---

### Post by mörgæs on 2015-10-16
New hardware should have the newest of software. 

While 14.04 is acceptable for old and semi-old hardware I think your gear deserves a fresh install of 15.10. 

Here is some more information:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)

---

### Post by Gregor D Seas on 2015-10-16
I would not suspect a hardware issues at this point. What the others have said are certainly useful option but I would suggest starting by running 'top' and seeing if there is something that is running and eating up cycles.

---

