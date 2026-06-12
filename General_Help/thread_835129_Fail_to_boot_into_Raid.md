---
title: "Fail to boot into Raid"
date: 2008-06-20
forum: General Help
---

### Post by Calida on 2008-06-20
Hi Folks,

I have installed (K)ubuntu on my new PC on a Raid. That was working a short time but now i have the problem that during the booting the booting stops and drops me to the busybox.

I got some error message saying

```
check root=bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
!ALERT /dev/md0 does not exist
```

I booted from a livecd mdadm --assemble --scan to see if the drives are okay. There it tells me that the superblocks of sda2 and sdb2 look very simliar and i should zero one out if they are different or remove one if they are. I did not really understud what that ment to be honest. Anyway i tried to get access by assembling sda2 and sdb2 which worked and i also was able to mount it afterwards. Everything is how it should be.

After rebooting i dropped back to the busybox :confused:

I looked through some stuff on the internet but i was not really able to find me some help so i hope you can advice me =)

thx

Calida

---

