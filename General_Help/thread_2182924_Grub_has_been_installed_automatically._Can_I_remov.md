---
title: "Grub has been installed automatically. Can I remove it?"
date: 2013-10-23
forum: General Help
---

### Post by hirotop2 on 2013-10-23
Hi, 

I was using a dell e6420 laptop with windows 7 installed. 
And I recently bought a SSD and removed the HDD and installed lubuntu 13.04 on SSD. 

Later, I realized that this laptop can use an external hard bay, where I can add external hard drive, I simply put the original HDD which has windows 7 installed. 

As both operating system is installed in different physical drive, and when I installed the lubuntu, the HDD was completely removed from the laptop,
the laptop does not operating in a dual boot system (no Grub). It simply boot from a drive that is the highest boot order in the BIOS. 

So, I could use both lubuntu and windows 7 by changing the boot order in the BIOS. 

I liked this way as it does not go through the grub (Usually grub takes 10 secs). 


But, today I realized that grub is installed all the sudden. I really don't know what happened. I want to remove it, but I am not sure whether it is safe to do that and whether it will put the system back into the original situation. 

I would really appreciate it if anyone could tell me what happened. 

Thanks,
hirotop

---

### Post by Dennis N on 2013-10-23
Grub was always on the SSD and its menu existed (with one OS - Ubuntu) whether you saw it or not. The menu was skipped by default because grub only had detected one OS when Ubuntu was installed  (since you had removed the HDD).
 
At some point, a new kernel was installed to Ubuntu. Part of that kernel upgrade process is to run update-grub. Since the HDD was now in the computer, grub scanned it as well as the SSD, found Windows, and added it to the menu. Since the menu now contained two OS, it is being displayed.

Added:

If you want to return to the old setup, disable the OS prober in Ubuntu and run update-grub. It should not find Windows and rebuild the grub menu without it. I think that will do it.

---

### Post by Dennis N on 2013-10-23
Simple way to disable the OS Prober using terminal commands:

```
cd /etc/grub.d
sudo chmod -x 30_os-prober
```

---

### Post by hirotop2 on 2013-10-23
It works and I could understand what was going on. 

Thank you so much. I appreciate it.

---

### Post by Dennis N on 2013-10-23
> **hirotop2 said:**
> It works and I could understand what was going on. 

Thank you so much. I appreciate it.

Success! Glad to learn you have restored the way you want it. It won't happen again as long as OS Prober is disabled. 

If you decide you need or want to have the Grub menu appear afterall, just enable the OS Prober again with **chmod +x 30_os-prober** and update-grub.

---

### Post by hirotop2 on 2013-10-23
Sure. Thanks!

---

