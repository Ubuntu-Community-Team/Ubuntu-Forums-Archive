---
title: "25secs to boot from SSD"
date: 2014-04-11
forum: General Help
---

### Post by marco_testa on 2014-04-11
Hello guys,

hope all of you are well,

I have just installed Ubuntu 14.04, although it is a beta, it's freaking stable and fast! The only annoying thing is the boot time.
My laptop has an i3 on board with 8gb of memory and a SSD, Windows 8 took only around 9 seconds, OSX86 Mavericks the same.. UBUNTU more than 25 seconds!
I am not really cleaver in these stuff, can someone please have a look to my bootchart image and let me know if there is any solution!?

Thanks!):P

---

### Post by zane99 on 2014-04-11
This image is way too low res to be evaluated.
Instead of attaching it, try uploading it to [http://www.minus.com/](http://www.minus.com/) and updating your thread.

---

### Post by oldfred on 2014-04-11
I never learned boot chart. 

But you can look in log files to see what may be slow. You may have log file viewer or:
 gksudo gedit /var/log/dmesg

Look only at errors, warnings, repeated tries at loading a driver, and anything with a long time between entries.

But my older slower SSD takes 25 sec from power on. It boots in 10 sec, but BIOS and grub take 15 secs. 

Are you using BIOS or UEFI? 

And is Windows using fast boot? That can cause dual boot issues, but it really is not booting but resuming from hibernation.

---

### Post by trag on 2014-04-11
Boot times of 22-25 sec. are not unusual from a fast SSD under old BIOS, 10-15 sec. under UEFI

---

### Post by marco_testa on 2014-04-12
Well, my laptop has BIOS but I guess bootchart start is charting at the loader; I have uploded my bootchart on my web hosting at [http://weebee.cc/imgs/bootchart.png](http://weebee.cc/imgs/bootchart.png)
Windows was booting in a normal way, no hibernation, the same OSX86.. Grub2 take about 3/4 secs the rest is ubuntu loading time. Dmesg seems to be clean...the cleanest I ever seen actually :)

---

### Post by KingLeonidas on 2014-04-12
I am using Ubuntu 12.04 LTS on Samsung ATIV Book 9 Plus NP940X3G and I had to change to CMS, UEFI was not recognizing the SSD. I don't think it's normal this time.

---

### Post by germanix on 2014-04-12
Keeping in mind that the final version of 14.04 is not out yet, I have noticed a slow-down in boot times between ubuntu 13.10 and 14.04 on my hardware. I have a Samsung 840 pro ssd. 13.10 boots in 10 seconds and 14.04 takes 15 seconds. On the other hand 13.10 took 15 seconds to shut down and 14.04 only 3 seconds. You win some, you lose some?. Have you checked which applications start at start-up?
Edit: My laptop uses Bios

---

### Post by marco_testa on 2014-04-14
> **germanix said:**
> Keeping in mind that the final version of 14.04 is not out yet, I have noticed a slow-down in boot times between ubuntu 13.10 and 14.04 on my hardware. I have a Samsung 840 pro ssd. 13.10 boots in 10 seconds and 14.04 takes 15 seconds. On the other hand 13.10 took 15 seconds to shut down and 14.04 only 3 seconds. You win some, you lose some?. Have you checked which applications start at start-up?
Edit: My laptop uses Bios

Nothing "extra" on start-up actually, I disabled bluetooth and cups. However you are right.. let's wait for the final version and we will see.

---

