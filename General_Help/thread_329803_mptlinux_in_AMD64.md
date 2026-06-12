---
title: "mptlinux in AMD64"
date: 2007-01-02
forum: General Help
---

### Post by baekmark on 2007-01-02
Hi there

I need to install mptlinux in order to get information from my LSI SAS HBA.

I found some information about mptlinux, but that was related to RH and SLES. Has anyone out there got this to work.

Linux visdom 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

[FONT="Courier New"]root@visdom:~/mpt# lsmod | grep mpt
mptsas                 30224  3
scsi_transport_sas     35328  1 mptsas
mptspi                 23184  2
mptscsih               31360  2 mptsas,mptspi
mptbase                61920  3 mptsas,mptspi,mptscsih
scsi_transport_spi     35200  1 mptspi
scsi_mod              181424  9 sg,st,sd_mod,mptsas,scsi_transport_sas,mptspi,mptscsih,scsi_transport_spi,libata
r[/FONT]

According to [http://www.drugphish.ch/~ratz/mpt-status/ReleaseNotes](http://www.drugphish.ch/~ratz/mpt-status/ReleaseNotes)
I need mptbase and mptctl to make this work

output from /proc/mpt/summary:
ioc0: LSI53C1030, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=177
ioc1: LSI53C1030, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=50
ioc2: LSISAS1064E, FwRev=010a0000h, Ports=1, MaxQ=511, IRQ=58

The hardware is a Sun Fire X2200 M2 with 2 Gig, and 2* SAS146 GB disks on a PCI-E LSIlogic HBA

Thanx in advance

---

### Post by imaswitcheryeah on 2007-05-04
Hi baekmark,

I'd love to help, but I need you to help me before I can help you! hehe :) 

What I mean by that is, I was searching these forums to find out if anyone had installed SAS HBA cards in their Ubuntu servers, as I am planning to do exactly that.  The crazy thing is, you have EXACTLY the hardware I am planning to get and the the same brand HBA.

I'm planning on buying a Sun Fire X2200 M2, installing a LSI SAS3801E HBA card with 2x4 external ports, and hook that up to a Dell MD1000 storage array.

I was wondering what you had to do to get it installed?  They have driver binaries for Red Hat and Suse, so I'm wondering how you got the card working in Ubuntu.

Any info would be much appreciated.  I promise once I get this hardware I'll help you out with your problem! ;)

Thanks a lot!
-Dan

---

### Post by rgaboury on 2008-01-07
Have you gotten anywhere with this problem?  I also have this configuration, and would like to set up the hardware raid.

Roland

---

