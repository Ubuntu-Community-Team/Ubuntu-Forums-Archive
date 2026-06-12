---
title: "GRUB broken...&quot;Minimal BASH-Like line editing is supported...&quot; on boot"
date: 2008-05-07
forum: General Help
---

### Post by cksubs on 2008-05-07
Hey all, I'm running a triple boot setup on my Macbook Pro (gen 2) with Leopard/XP/Ubuntu8.04

Triple boots on Macs use a bootloader (correct term?) called rEFIt to make the necessary EFI/BIOS boot combination required by the various operating systems.

The problem is the GRUB stacks on top of this and causes a lot of problems. After installing Ubuntu my XP partition started using GRUB (after rEFIt) as well, even though I installed GRUB to Ubuntu's / partition. Eventually, after several reboots, both XP and Ubuntu returned the "Minimal Bash-like..." error on boot. This has happened before, and I've always in the past formatted the Ubuntu drive to get it working again in XP. This time though I want Linux working. I went into the XP recovery CD console and used the command "fixmbr" to fix the Windows partition. It now boots correctly. But Ubuntu still will not boot. What should I do?

---

### Post by cksubs on 2008-05-07
Anyone?

---

