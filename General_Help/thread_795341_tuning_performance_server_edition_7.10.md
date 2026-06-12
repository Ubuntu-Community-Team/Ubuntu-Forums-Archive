---
title: "tuning performance server edition 7.10"
date: 2008-05-15
forum: General Help
---

### Post by 02dag on 2008-05-15
I have installed 7.10 server edition on an AMD 64 dual core 3.2 GHZ with 4GB RAM. I am running the OS on a 10GB IDE disk. I have installed Vmware server beta 2.0 and have 5 VMs on a 160GB mirrored disk. The RAID is a hardware RAID on an adaptec 2420SA with 128 MB rAm. In addition to this I will be running the ubuntu as a file server with 2x500GB mirrored.

Currently I have no files on the 2x500GB disks, but I am running 5 vms and the performance is reeaaally sluggish.

Is there a way to tune the system a bit. The VMs are doing nothing. I have a w2k8 core as dc, a w2k8 CAS, w2k8 HUB and a w2k8 MBX. in addition I run an w2k3 ISA and a w2k3 SMTP gateway. They all have 512 MB of RAM. 5x512 should be 2500

This is the output of the free command

dag@fjvms:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3938         24          0         84       2975
-/+ buffers/cache:        878       3084
Swap:          454          0        454

What is using all the memory?

---

### Post by pointone on 2008-05-15
```
top
```

How much memory have you allocated to your VMs?

---

### Post by 02dag on 2008-05-16
I have allocated 512 on each vm -> 2,5 GB. According to Vmware they are using only 0,5 GB in total.

Also ran the cat /proc/loadavg and got 53% as an avg even though it was doing nothing.

---

### Post by pointone on 2008-05-16
I think you missed the first part of my post. 

Please run the "top" command to see which processes are using the most memory/CPU.

---

