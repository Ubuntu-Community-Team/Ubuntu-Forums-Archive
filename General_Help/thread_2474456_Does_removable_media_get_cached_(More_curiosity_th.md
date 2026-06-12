---
title: "Does removable media get cached? (More curiosity than help needed)"
date: 2022-04-29
forum: General Help
---

### Post by punx45 on 2022-04-29
So a weird thing just happened. I had a micro SD card that I have used a bunch on this system, then lost, and replaced with another of the same size and brand (MicroCenter 32GB). Today I took the new micro sd card straight out of the sealed package that I just received from Amazon yesterday, placed it directly into my FPV goggles where it stayed until just now when I took the card out, and put it in my computer to get the footage I recorded today. 

Here's where the weird stuff starts: the brand new card had ALL of the data from the lost card, and it was readable. I played the very first AVI file recorded months ago right off the card

So, does Ubuntu cache removable media, and it just got tricked into thinking this was the same card? Did my lost card somehow wind up in new packaging and sent to me :) ?  Something else? 

(no i don't think the goggles stored anything, they were only $80 and have no internal storage as far as I know. Also I had used the card in my fire tablet several times, so all the Amazon/Android folder stuff was on the replacement card too)

I'm running Impish on a Lenovo T480.

```
geoff@tp:~$ hostnamectl
 Static hostname: tp
       Icon name: computer-laptop
         Chassis: laptop
      Machine ID: ecabcacda0174b2399007493835b59e5
         Boot ID: 2972d4a81f8e4b88a375ecb3b518b439
Operating System: Ubuntu 21.10                    
          Kernel: Linux 5.13.0-39-generic
    Architecture: x86-64
 Hardware Vendor: Lenovo
  Hardware Model: ThinkPad T480
geoff@tp:~$ uname -a
Linux tp 5.13.0-39-generic #44-Ubuntu SMP Thu Mar 24 15:35:05 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

EDIT: wow, i havent been on here in YEARS and love that ubuntu one matched up with my old profile instantly (that sig is SUPER out of date!)

---

### Post by guiverc on 2022-04-29
Yes removable media data can be cached.

I've in error overwritten the start of an external drive using `dd`  (*trying to write an ISO to thumb-drive but mistakenly giving it the wrong device* *so it wrote over an external 2TB drive instead of 8GB usb-stick*)  ...  

The `dd` caused the first ~2GB to be overwritten which included a large amount of the directory data/partition table of my disk, but I quickly realized what I did & was able to use the *cached* data to get a huge % of my data off the disk successfully.

If you eject the drive, the *cached *data will be dropped (*I believe*), and I'd not expect any cache to survive logout/reboot etc, but if you didn't eject the device & still had the same session running, and your system wasn't running short on RAM (*thus space used for caching will be reused for other things & cache is lost*) it can survive (cached) for some time.  It allowed me to resurrect most of my 2TB data without needing to resort of photorec/testdisk

---

### Post by punx45 on 2022-04-29
so not only has the original drive been ejected (its been lost for weeks) my system had been powered off at least once since the last time it had been inserted...

```
geoff@tp:~$ uptime
 22:43:32 up  2:57,  1 user,  load average: 1.18, 1.11, 0.92

```

---

