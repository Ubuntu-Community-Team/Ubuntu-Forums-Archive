---
title: "Compatibility between different RAID controllers"
date: 2008-04-07
forum: General Help
---

### Post by rm-rf on 2008-04-07
So RAID 5 is highly reliable because the likelihood of two disks failing is low... But then again; what if your RAID controller fails? 

I'm building a new system ([with this motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131244")). I'm putting a ton of disks (about 12, I will be using a SATA port multiplier to get me there) which I would like to configure as RAID 5 plus the OS disks as RAID 1 (mirroring). The question is; if the motherboard dies, will another RAID controller let me access my RAID 5 disks? Before I put all my eggs on the RAID-5 basket, I really would like to make sure that the motherboard is not my single point of failure.

I would like to use hardware RAID for its alleged superior performance, which may in fact not be the case with the RAID controller that my motherboard has...

So the questions are:
[LIST]
[*]If the motherboard dies, will another RAID controller be able to read the drives?
[*]Will the 'hardware' RAID controller on the motherboard be significantly better than straight Linux software RAID?
[/LIST]

If you care to speculate it would be greatly appreciated. Thanks in advance.

---

### Post by fjgaude on 2008-04-07
Using motherboard raid controllers is really the same as using software raid in Linux, for the CPU and the PCI-e bus are the items that do the work.

I've used software raid5 for about two years without issues. I've moved to another motherboard, AMD to Intel, during that time and the raid5 array started up without a problem.

If motherboard fails, no problem. Buy another and the software raid starts up with a simple command, --assemble --scan, using mdadm program. Under both Gutsy and Hardy md works perfectly, bootup to bootup.

I have a Gigabyte P35 MB and don't use the onboard raid, as that would require me to use dmraid which is something that is not that well supported in Linux. It works but is not to my liking.

---

