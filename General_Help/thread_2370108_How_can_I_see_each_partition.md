---
title: "How can I see each partition?"
date: 2017-08-30
forum: General Help
---

### Post by eureka117 on 2017-08-30
On my disk I have quite a few partitions. I originally installed my copy of Linux along side windows 8 and then "upgraded" to windows 10.  When I look at my partition table it looks terrible! I have no clue what's on most of these partitions. So I'd like to know if there is an easy way I can differentiate between each partition. 

I know that (hd0,7) is my Linux volume and I believe (hd0,6) is my (probably poorly installed) GRUB boot loader. 

Attached is a screen shot I took of gparted and my ~/home/ folder. As you can see my /home folder is pretty full and I'd like to clean it up. The problem is I need to extend this partition. If you're wondering why I haven't already extended it, it's because when I tried earlier it moved a few blocks. Then when I tried to boot back into Linux I was met with the grub rescue> menu. Ultimately I'd like to clean up my partition table so I only have the bare minimum. I want to have as few partitions as possible so I can maximize my Linux volume.

---

### Post by oldfred on 2017-08-30
Windows with UEFI has multiple partitions.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-]("https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference")

But your drive is in effect full.
Windows really needs 30% free to run well. At 10% free, you just about cannot do a defrag.
Linux does not need quite as much free space but still works better if you have more free space than you have.
Either a lot of backup & major housecleaning or a new larger hard drive would be best alternatives.

---

