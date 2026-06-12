---
title: "System starts failing when RAM is low"
date: 2008-05-20
forum: General Help
---

### Post by FFighter on 2008-05-20
When have some heavy applications opened at the same time, my system starts failing. X starts ignoring keyboard shortcuts (for example, CTRL+S on Eclipse won't save anymore, but will simply output "S" to the text area of Eclipse) and deadkeys, other apps will start but exit after a while without warning, the sound will stop working and other annoying things.

I'm pretty sure it has to do with low RAM memory. I have 2GB on this laptop. The swap partition is of 2GB of size.

I usually have a VMWare Workstation instance opened all the time, running XP with Photoshop, Flash and other apps. This VM is allowed to eat up to 1GB of RAM. I acknowledge the VM can get heavy, but the issues I get when system memory is low are really annoying.

I was thinking about using another, lighter DE. But I really like Gnome. I would love to know if there are any other ways I could go to help the system to eat less memory and thus making more memory available to the apps that help me get things done ;)

---

### Post by bingoUV on 2008-05-20
2GB should be much more than enough.
Post the output of the following when the system is in such a state.
```

cat /proc/meminfo

```

See if the below helps. You have to run it at every boot.
```

sudo echo 10 > /proc/sys/vm/swappiness

```
If you like the behaviour after this, put this line in /etc/rc.local.

---

### Post by sdennie on 2008-05-20
If you have 2G of RAM and are only giving 1G to VM's that's probably not the problem (1G of RAM is more than enough to run Ubuntu efficiently).  Do you ever have that problem without the VM running?  If not, maybe try a different virtualization software.  I use VirtualBox and have 2-3 VM's up at the same time (except when on battery) and I notice no slowdown whatsoever on my machine.

---

### Post by FFighter on 2008-05-20
> 2GB should be much more than enough.
Post the output of the following when the system is in such a state.

```

MemTotal:      2066436 kB
MemFree:        134020 kB
Buffers:         56044 kB
Cached:        1174892 kB
SwapCached:      47476 kB
Active:        1404728 kB
Inactive:       363668 kB
HighTotal:     1170240 kB
HighFree:        41980 kB
LowTotal:       896196 kB
LowFree:         92040 kB
SwapTotal:     2931852 kB
SwapFree:      2795236 kB
Dirty:            2064 kB
Writeback:           0 kB
AnonPages:      535416 kB
Mapped:         778568 kB
Slab:            64144 kB
SReclaimable:    47200 kB
SUnreclaim:      16944 kB
PageTables:       4356 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   3965068 kB
Committed_AS:  1413452 kB
VmallocTotal:   114680 kB
VmallocUsed:     10236 kB
VmallocChunk:   103520 kB

```

Also in the link below is the output of ps -Al (I thought it might be useful), I've posted it externally in order to not pollute this post:

[http://www.pastebin.ca/1024137]("http://www.pastebin.ca/1024137")


> If you have 2G of RAM and are only giving 1G to VM's that's probably not the problem (1G of RAM is more than enough to run Ubuntu efficiently). Do you ever have that problem without the VM running? If not, maybe try a different virtualization software. I use VirtualBox and have 2-3 VM's up at the same time (except when on battery) and I notice no slowdown whatsoever on my machine.

It usually only happens when I have the VM running, though I think I can remember two or three times when FireFox did something similar.

> See if the below helps. You have to run it at every boot.

Could you explain me what does it do exactly ?

Thanks.

---

### Post by bingoUV on 2008-05-21
It reduces the tendency of the system to use swap memory. Default is I think 60. For high RAM desktop systems, it generally improves responsiveness if it is lower than that. Even 0 is acceptable for such systems. Try what suits you.

Read [http://www.linuxinsight.com/proc_sys_vm_swappiness.html](http://www.linuxinsight.com/proc_sys_vm_swappiness.html).


I see in your meminfo that although the memory is full, a lot is cached. This is freed immediately as programs require memory so you have almost 1GB free memory in that sense. Swap usage is negligible , the little that is used is swap cached so speed should be quite high for that too.

---

