---
title: "Ubuntu 20.04 Suspend resume does not work"
date: 2021-02-15
forum: General Help
---

### Post by emilio-11 on 2021-02-15
I've been using ubuntu for a while and I've never  encountered a problem. However,after suspending the laptop, when I try  to resume screen goes for blank(Neither mouse nor keyboard action  works).


 I've tried several solutions posted here but none of them worked like  editing grub file for AMD/Nvidia drivers, doing hardware  troubleshooting(no problem in hardware).
 After carefully examining /var/log/kern.log I've noticed that this below message:


 ***BIOS may not properly restore RDRAND after suspend, hiding RDRAND via CPUID. Use rdrand=force to reenable***

 I assume it is because of upgrading kernel to the new version. But I don't know how to resolve this. Any ideas are welcome

 
System Details:

 
[LIST]
[*]OS: Ubuntu LTS 20.04, Kernel 5.8.0-43-generic 
[*]CPU: AMD A6-6310 APU with AMD Radeon R4 Graphics 
[*]GPU: Mullins [Radeon R4/R5 Graphics] 
[*]RAM: 8GB 
[/LIST]

---

