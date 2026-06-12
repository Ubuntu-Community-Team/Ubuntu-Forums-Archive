---
title: "Ubuntu 7.10 freezes at start up"
date: 2008-01-05
forum: General Help
---

### Post by brunodf on 2008-01-05
i've just installed ubuntu on my hp laptop, when i restarted my computer and tried to start ubuntu it froze about 1/5 of the way, i've only been able to start ubuntu twice. can anyone help please.

---

### Post by sports fan Matt on 2008-01-06
How far does Ubuntu get before it freezes? and when you say "start ubuntu twice, does it in those 2 instances reach the login ubuntu screen where you are prompted for a username and password?

---

### Post by brunodf on 2008-01-06
it gets to about 10 % before it freezes, and yes i made it to the login in screen twice where everything worked fine, but when i tried to restart, it would freeze again.

---

### Post by anthonyJC on 2008-01-06
maybe a bug in bios implementation of acpi 2 specification, some bioses don't implement it correctly, move down to acpi one in bios. i think but do not know for sure, doesn't show in xp since it only uses acpi 1 spec but linux uses acpi 2 spec.(is it an xp laptop?) if this doesnt solve it, post again and i'll give some hints on how you can get the kernel hang logs.

---

### Post by brunodf on 2008-01-06
i don't see any acpi in my bios, and my laptop is running vista, i have a dual boot system now.

---

### Post by anthonyJC on 2008-01-06
So I guess the livecd works fine for you to have installed ubuntu on the computer? Or you installed Ubuntu using a different machine, then transfered the hard disk to the HP laptop?; if not - maybe the solution lies in the default kernel options used to boot the liveCD. If it's not the kernel causing the freezing then ALT+PRTSCN held down then type RSEIUB, allows possibility of faulting kernel module to be listed in syslog, then use livecd to find the faulting kernel module.  if the livecd freezes you need to burn a rescue livecd, find one using distrowatch.com. A gutsy Livecd that freezes on your machine unless it is passed boot option "noacpi" would show a acpi2 bios bug to be the cause. I don't have enough GRUB experience to fix your installation.

---

### Post by Gillette on 2008-01-06
I had this problem last week. Someone suggested I clean the dust out of my computer. I found it was very dusty and I blew out the dust with a can of compressed air and the problem went away. They said for some reason Ubuntu is less tolerant of dust then microsoft windows.

---

