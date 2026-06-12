---
title: "Gnomebaker"
date: 2005-04-10
forum: General Help
---

### Post by razor_88 on 2005-04-10
I'm trying to burn a cd in gnomebaker but I keep geeting this error.  ](*,) 

[http://img235.exs.cx/img235/6338/screenshot2fz1.png](http://img235.exs.cx/img235/6338/screenshot2fz1.png)

I tried running readcd -scanbus as root but I got this error. 

root@c211-28-168-250:/home/ryan # readcd -scanbus
readcd: No such file or directory. Cannot open SCSI driver.

---

### Post by clparker on 2005-04-10
Well, does K3B work? I only suggest trying that to see if it might me a hardware/system problem, not a GnomeBaker Thing....

---

### Post by razor_88 on 2005-04-10
I tried k3b but I still get the same error.

---

### Post by fordfan753 on 2005-04-10
I think you need to set up SCSI emulation...I don't know exactly how to do it, but look around google a bit for how-tos on SCSI emulation.

---

### Post by razor_88 on 2005-04-10
[QUOTE=fordfan753]I think you need to set up SCSI emulation...I don't know exactly how to do it, but look around google a bit for how-tos on SCSI emulation.[/QUOTE]

Thanks fordfan753 It works perfectly now.  \\:D/ 

BTW heres the page that tells you how to enable SCSI Emulation 
[https://www.ubuntulinux.org/wiki/HowToEnableSCSIEmulationWithHoaryKernel26/diff](https://www.ubuntulinux.org/wiki/HowToEnableSCSIEmulationWithHoaryKernel26/diff)

---

