---
title: "Nexus 4 file system no longer mounts to Ubuntu 12.04"
date: 2013-06-06
forum: General Help
---

### Post by Stef700 on 2013-06-06
My Nexus 4 had worked a treat connecting with Ubuntu 12.04 via USB. It's worked flawlessly for months but has just recently broken...

If I plug my phone into either Windows XP or Ubuntu 12.04 the phone shows "Connected as a media device"

My XP Laptop flawlessly auto mounts the phone file system when I connect it via USB cable

My Ubuntu Desktop NO LONGER auto mounts the phone file system when I connect it via USB cable 
(Nothing shows under home folder any more - The phone file system *used to* 'pop up' and mount when connected)

Memory sticks still work fine on these Ubuntu USB ports (I have tried two). I have also tried two cables (XP works, Ubuntu does not)

Any help much appreciated,

Many thanks,
Stefan

Ubuntu 12.04 64 bit (Pentium quad core)

---

### Post by Isamu715 on 2013-06-06
Did you upgrade to Android 4+ on your Nexus 4 recently? Since version 4 Android uses MTP to connect to PCs which is not supported in Ubuntu 12.04. If you want MTP support you need to either update to Ubuntu 13.04 or install a newer version of GVFS with:
```
sudo add-apt-repository ppa:langdalepl/gvfs-mtp
sudo apt-get update
sudo apt-get upgrade
```
I did it that way and my Nexus 7 connects flawlessly.

---

### Post by Stef700 on 2013-06-06
> **Isamu715 said:**
> Did you upgrade to Android 4+ on your Nexus 4 recently?

Not afaik - the phone is currently running Android 4.2.2 and has been running Android 4 since I took it out of the box in Jan...

 > **Isamu715 said:**
> Since version 4 Android uses MTP to connect to PCs which is not supported in Ubuntu 12.04.

Will bizzaro or whatever but it worked just fine and only recently stopped working.... 

 > **Isamu715 said:**
> If you want MTP support you need to either update to Ubuntu 13.04 or install a newer version of GVFS with:
```
sudo add-apt-repository ppa:langdalepl/gvfs-mtp
sudo apt-get update
sudo apt-get upgrade
```
I did it that way and my Nexus 7 connects flawlessly.

Thanks I did that and it now works again even slightly slicker (It now  says NEXUS4 against the DEVICE icon)

Thanks again...

Stef :D

---

