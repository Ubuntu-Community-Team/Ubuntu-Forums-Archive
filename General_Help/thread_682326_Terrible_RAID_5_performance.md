---
title: "Terrible RAID 5 performance"
date: 2008-01-29
forum: General Help
---

### Post by Dalmaris on 2008-01-29
Hi,

I have created a RAID 5 array using mdadm using 3 320GB sata drives, with 2 of them been connected to the motherboard and the third connected to a pci sata card. I have run various benchmarks using bonnie++, dd & hdparm and everything seems to be fast but when i try to copy files to/from the array either from the OS drive which is a pata drive connected to the motherboard or to another computer on the network it copies extremely slow. It seems to copy at about 3MB a second which is pretty terrible, I even tried different filesystems /ext3/xfs/reiserfs but it makes no difference. I have another old PATA drive i use for testing so i put that in and installed OpenSuse 10.3 and mounted the array and it works much much faster. 
I also tried Debian 4.0, Centos 5.1 and Fedora 8 with Centos & Debian also working fine but Fedora exibiting the same problems as Ubuntu 7.10. As this is my desktop machine i would prefer to keep running Ubuntu but if i can't fix this problem I may have to use something else. I also install the ubuntu server edition kernel but that did
't make a diffenrece. Does anyone know what could be causing these issues?

thanks

---

### Post by pjkoczan on 2008-01-30
RAID 5 tends to be slow for writing. The parity calculations take up a lot of time, but that doesn't account for that level of slowness.

> when i try to copy files to/from the array either from the OS drive which is a pata drive connected to the motherboard or to *another computer on the network* it copies extremely slow. It seems to copy at about 3MB a second which is pretty terrible, I even tried different filesystems /ext3/xfs/reiserfs but it makes no difference. I have another old PATA drive i use for testing so i put that in and installed OpenSuse 10.3 and *mounted the array* and it works much much faster.

I'm guessing you mounted the array locally on your OpenSuse test. I think your bottleneck is the network. Check to see what kind of network throughput you're getting (hint: it should be around 3 MB/sec).

So, how do you fix this?
- Get on a faster network (Gigabit, probably), though I doubt that's readily available to you.
- Use the array locally when you need performance, and expect poor performance when going over the network.

The problem likely wasn't with your operating system or your file system, it was with the data path.

---

### Post by Dalmaris on 2008-01-30
sorry i think you misunderstood the problem.

file server is setup as follows

PATA OS Drive - Ubuntu 7.10

Raid 5 array containing

Sata MB - 320GB
Sata MB - 320GB
SATA Pci card - 320GB

when i run benchmarks on the array it is fine

Reads 140MB's
Writes 65MB/s

when i try copy to/from the array to another drive in the same system or another system on the network i get 3MB/s - 5MB/s. If i replace the OS drive with another drive with opensuse/debian/centos or boot a live cd of one of those then i get 140MB/60MB/s when copying to/from the array to another disk in the system or 30MB/s over the network which is gigabit. 

So the problem is a Ubuntu problem as the array is fast on those other distros.

thanks

---

### Post by dcstar on 2008-01-30
> **Dalmaris said:**
> 
.......
So the problem is a Ubuntu problem as the array is fast on those other distros.

thanks

Can you list what kernel versions run fast and slow?

---

### Post by Dalmaris on 2008-01-30
Ubuntu - 7.10 - Kernel 2.6.22 - Slow
Fedora 8 - 2.6.23 - Slow
OpenSuse 10.3 - Kernel 2.6.22 - Fast
Debian 4.0 - 2.6.17 - 2.6.17 - Fast
Centos 5.1 - 2.6.17 - Fast

thanks

---

### Post by pjkoczan on 2008-01-30
B'oh. I did misinterpret your post. Sorry.

Given that the problem occurs regardless of filesystem, I can think of two other things offhand. The RAID software might be causing a bottleneck, or the system doesn't like the PCI SATA card (It might be using a poor choice of driver and creating a bottleneck).

Two things you should try.

- Try testing the array as a RAID 0 array. RAID 0 is inherently faster, so you should get some performance benefit. If you don't get what you expect (meaning it's still hovering around 5-7 MB/sec), then it's not the RAID software. Be sure to change it back to RAID 5 when you're done, as RAID 0 offers no protection against disk failure.

- Check out the output of /sbin/lspci and /sbin/lsmod (list PCI devices and list kernel modules/drivers, respectively). Be sure to compare the output of your ubuntu box to that of your opensuse box. I don't know exactly what you should look for, except maybe things related to libata, and especially look for any discrepancies.

Hope this helps.

---

