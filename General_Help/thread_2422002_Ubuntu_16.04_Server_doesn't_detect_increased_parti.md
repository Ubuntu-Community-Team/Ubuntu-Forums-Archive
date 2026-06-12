---
title: "Ubuntu 16.04 Server doesn't detect increased partition size after altering in GPART"
date: 2019-06-30
forum: General Help
---

### Post by mikeaw2010 on 2019-06-30
Running Ubuntu 16.04 Server on a ESXI VM Server.

I ran out of space and needed to increase the size of my partition:
[IMG]https://i.postimg.cc/Vvd8qk3b/Ubuntu-Server-Space.png[/IMG]

I increased the storage capacity by 64 GB's in ESXI and then by using GPART supplied in the Ubuntu 16.04 Desktop Image - of which I installed as an ISO onto the ESXI datastore and loaded it from a virtual CD-ROM ran it off the disk...
[IMG]https://i.postimg.cc/gJMpLZBW/GPartedit.png[/IMG]

I apply the changes and it goes through quickly, GPART sees the additional space as allocated and unused, however; after rebooting, Ubuntu Server still sees the same partition as completely maxed out with no unused space just as it did in the first image like I never did anything.

[IMG]https://i.postimg.cc/Vvd8qk3b/Ubuntu-Server-Space.png[/IMG]

Any help would be appreciated it.

---

### Post by TheFu on 2019-06-30
You are using LVM, so you'll need to pvresize, vgextend and lvextend assuming the partition actually is larger.

Run an **lsblk** to see the layout. Then run 
```
sudo pvs
sudo vgs
sudo lvs

```to see how the 3 different LVM parts are connected on YOUR system.  The formal commands are pvdisplay, vgdisplay and lvdisplay, but the summary versions above are all I've needed since those commands became available. They get to the point/data we need to manage LVM storage.

LVM uses those physical and abstract organization "objects" to provide huge flexibility.
Perhaps a diag would help?
```
DISK1
&#9492;&#9472;&#9472; partition-1
    &#9492;&#9472;&#9472; PV-a
        &#9492;&#9472;&#9472; **VG-a**
            &#9500;&#9472;&#9472; LV-1
            &#9500;&#9472;&#9472; LV-2
            &#9492;&#9472;&#9472; LV-3
DISK2
&#9492;&#9472;&#9472; partition-1
    &#9492;&#9472;&#9472; PV-b
        &#9492;&#9472;&#9472; **VG-a **

```
PVs are limited to a specific partition.
VGs are made up of 1 or more PVs.
LVs are allocated from a VG without understanding exactly which physical PVs are involved.

Linux LVM is basically the same as every other volume management solution for every  other platform. The only difference is that 
PV == PE.  
Physical Volume == Physical Extents.

Clear as mud?

After you increase the size of the disk in the hypervisor, then you have options around increasing the partition size or just creating a new partition in the extra space. Because of LVM, it really doesn't matter which you choose.  If you go with the later method, use pvcreate using the new partition, then add that new PV to the same VG you already have, and finally, extend the LV(s) you want to be larger using lvextend -r -L +20G ....  

BTW, I wouldn't have the root LV larger than 25G. Only the OS should go into that area.  Then I'd create other LVs for all the non-OS stuff like DBs, websites, container-stuff and data files.  With LVM, you can resize up in about 5 seconds, so there isn't any need to over allocate "just-in-case."

LVM is freakin' awesome!

And when it comes time to migrate a VG or LV to a new disk, there are commands for that which work on live file systems.  To get a feel for which commands LVM has, use tab completion.

pv{tab}{tab}
vg{tab}{tab}
lv{tab}{tab}

---

### Post by mikeaw2010 on 2019-07-05
Thanks, with this I was able to solve the issue.

---

### Post by TheFu on 2019-07-05
> **mikeaw2010 said:**
> Thanks, with this I was able to solve the issue.

Please help the community and mark this thread as SOLVED using the "Thread Tools" button near the top.
Help people looking for solutions and others not to waste time.

---

