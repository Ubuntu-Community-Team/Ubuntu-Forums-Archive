---
title: "ARRAYS not being assembled anad lvmetad not running"
date: 2019-04-05
forum: General Help
---

### Post by rsteinmetz70112 on 2019-04-05
I had a running 18.04 LTS system. I broke something and now I can't get it to boot. On boot up it drops into the initramfs shell after saying ti can't connect to lvmetad.

I can't get any further from there. The Linux volumes are in a mdadm array which is not starting. I get an error that no devices in the configuration file can be found. mdadm -A --scan does not find any thing. vgscan does not find anything. 

I read through a lot of previous posts but haven't found anything on point. I can boot into a live session and assemble the ARRAYs, then scan the Volume Groups and even update initramsfs, but I still can't boot.

It appears not of the harde drive (sd)  devices are in /dev of the initramfs shell.

---

### Post by rsteinmetz70112 on 2019-04-08
Please see my other thread. Something messed up the system modules that create the sd devices in /dev. I reinstalled a bunch of packages and everything now works.

---

