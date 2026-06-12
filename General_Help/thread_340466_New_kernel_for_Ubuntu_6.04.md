---
title: "New kernel for Ubuntu 6.04"
date: 2007-01-17
forum: General Help
---

### Post by frspin on 2007-01-17
I run a server with Ubuntu 6.04 made up to date .
Now I need a new kernel for getting my Sata PCI card work ok. Current version of kernel (2.6.15-27) use my SATA card but I get some timeout errors with heavy read load.

For testing new kernel I have removed my SATA card and put in another machine, running 6.10, get a 2.6.19.2 source kernel (from kernel.org), compile it and all is now ok. So I need almost 2.6.19.2 kernel for my server. Recent upgrade (2.6.18) of libata made my card correctly working.

On my server, running Ubuntu 6.04, I get same kernel source, use same kernel config file, compile & install kernel without any problem.
At boot time all my disk are correctly detected but I can use only my hda (boot) disk. All other (hdc, sda) are in /dev but can't be used. If I use it for mount (i.e. mount /dev/hdc1 /some_point) I get an error with "disk already mounted or busy".
I suppose a problem with udev and so.
What is changed from 6.04 to 6.10 in using disk?
Upgrading server to Ubuntu 6.10 is not an option.

My server hardware is a Supermicro board with 2 Xeon CPU and 4 Gb RAM, 2 IDE disk , 1 SCSI disk and 2 SATA disk on PCI card.
My test hardware was an Asus board with a Core 2 Duo CPU, 1 Gb Ram, 1 SATA disk on motherboard and 2 SATA disk on PCI card. 

Regards

Franco

---

### Post by wnelson on 2007-01-17
There are instructions in the HOWTO section on manually upgrading you kernel. Yet, before you do that you may want to see if there any dependency that need to be meet first.  I think there are some UDEV changes that may help also with you SATA issues along with the new kernel. You may want to re-think the upgrade to 6.10?

Walt

---

### Post by frspin on 2007-01-18
Solved !

Was a EVMS problem. At startup EVMS get control of my local disk but not for my boot disk.
I don't use EVMS so I removed it.
Now all my local disks are usable

Franco

---

