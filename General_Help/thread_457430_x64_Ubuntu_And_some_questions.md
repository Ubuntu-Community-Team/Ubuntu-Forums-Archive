---
title: "x64 Ubuntu? And some questions"
date: 2007-05-28
forum: General Help
---

### Post by spaceship9 on 2007-05-28
1.) when/can wubi support x64 Ubuntu? Because I have an x64 CPU but I don't want to "kill" XP by doing a "real" installation of Ubuntu. I placed the x64 ISO in the same directory as Wubi but it didn't recognize it and started to download the regular x86 ubuntu
2.) Is there a way to be able to choose to install all the "custom" packages in Ubuntu Studio?
3.) When I try and setup wifi in Ubuntu Studio, it looks like it works, but then it doesn't connect, even with hte right pass. I tried all the encryption formats and both open and shared key... None worked. Then after a few tries the system "freezes".. upon reboot, the virtual disk is "unconnectable"
4.) Is there away to use Wubi with another OS other then Ubuntu? (Like Fedora 6)

Thank you!

---

### Post by ago on 2007-05-28
> **spaceship9 said:**
> 1.) when/can wubi support x64 Ubuntu? Because I have an x64 CPU but I don't want to "kill" XP by doing a "real" installation of Ubuntu. I placed the x64 ISO in the same directory as Wubi but it didn't recognize it and started to download the regular x86 ubuntu
Soon, hampus has a 64 bit machine so he will be able to work on it, I'll do the other required changes. 

> 2.) Is there a way to be able to choose to install all the "custom" packages in Ubuntu Studio?
If you use the latest minefield they should be all installed by default

> 3.) When I try and setup wifi in Ubuntu Studio, it looks like it works, but then it doesn't connect, even with hte right pass. I tried all the encryption formats and both open and shared key... None worked.
You should see the general forum for that

> Then after a few tries the system "freezes".. upon reboot, the virtual disk is "unconnectable"
Hard reboots can corrupt the filesystem. You should always try to avoid them. See alt+sysrq key combinations in linux.

> 4.) Is there away to use Wubi with another OS other then Ubuntu? (Like Fedora 6)
The same technique can be applied to other distros. Debian based distros are supported almost out of the box. For other distros more work is required and we do not have the resources to do that, but our project is open source and we would be glad for others to find uses for it.

---

### Post by spaceship9 on 2007-05-28
thank you for the fast reply!

---

