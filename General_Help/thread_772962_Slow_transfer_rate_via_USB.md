---
title: "Slow transfer rate via USB"
date: 2008-04-28
forum: General Help
---

### Post by niol01 on 2008-04-28
I have horrible transfer speeds to my usb hard drive and my usb stick, write speed is around 2 Mb/sec and read speed is around 10 Mb/s. Its not a hardware issue because I get great speeds when running XP on the same computer.

I get the following message in dmesg: 

"new high speed USB device using ehci_hcd and address 3"

so the USB devices are recognized as USB2.0. I also checked so they are not mounted with the sync option.

Anyone have any ideas how to troubleshoot this ?

---

### Post by danwood76 on 2008-04-28
Well 20MB/s is a theoretical max for USB Hard disk data transfer, no matter what the manufacturers quote. (480Mb/s is ~60MB/s)
USB sticks will be slow as they have flash memory in them, which is slow.

10 MB/s isnt bad and is better than USB1.1, what speeds do you get in windows?

-- edit --

Whoops, I read 10 MB/s as write speed.
Sorry, you are definitely running faster than USB 1.1 though.
Im assuming your running XP.

Whats the spec of your system and what USB disk is it?

---

### Post by niol01 on 2008-04-28
I have a IBM Thinkpad r50e, Intel 1.6ghz processor, 1GB ram. The USB disk is a Lacie desktop 320 GB drive.

I haven't clocked the transfer rate when running XP but its A LOT faster than Ubuntu (8.04).

I appreciate your help !

---

### Post by danwood76 on 2008-04-28
When you say a lot faster how are you gauging it?
For example transfering the same file and timing?

I would expect Hard Heron (8.04) to use more RAM and processor overhead than XP.
Afterall XP is an old OS (2001) which could account for the slower transfer rates.

Lacies are normally pretty quick in my experiance, and 2MB/s on a USB hard disk is slow.
Is there anything hogging your CPU time when doing file transfers?
in terminal run the following command and post the output in the middle of a transfer:
```

top

```

---

### Post by niol01 on 2008-04-28
My top output

```
5118 root      20   0  297m  79m 6376 S  6.3 16.1  34:32.45 Xorg               
 5814 niol01    20   0 35536  13m 8148 S  4.2  2.7   9:43.91 transmission       
14415 niol01    20   0  2308 1120  856 R  4.2  0.2   0:00.14 top                
 5482 niol01    20   0 94376  29m  14m S  2.1  6.0   1:22.48 nautilus           
 5552 niol01    20   0 26648  10m 6392 S  2.1  2.1   4:11.20 compiz.real        
    1 root      20   0  2844  528  476 S  0.0  0.1   0:01.32 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.20 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.56 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   42 root      15  -5     0    0    0 S  0.0  0.0   0:01.60 kblockd/0          
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  122 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            
  155 root      15  -5     0    0    0 S  0.0  0.0   0:07.80 kswapd0  
```

I've checked the transfer rate with the same 700 MB iso file, with XP it takes around 1 minute to transfer with ubuntu 6 minutes.

---

### Post by danwood76 on 2008-04-28
What you could try is killing the compiz.real process and switching off transmission (bit torrent client) and try the transfer again.
That should increase the transfer speed, it could also be lag due to the NTFS filesystem, which I assume your USB disk is using.

---

