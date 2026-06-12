---
title: "Kernel Panic on reinstall"
date: 2007-07-07
forum: General Help
---

### Post by rpalmeri on 2007-07-07
After corrupting my files in kubuntu (trying to get two video cards to work- don't ask...) , I uninstalled wubi, and reinstalled it. While it originally worked fine, now whenever I try to boot into ubuntu to finish the installation, I get a message "Kernel panic- not syncing:VFS: Unable to mount root fs on unknown-block (104,1)
I have uninstalled and reinstalled several times, proving the saying that madness is trying the same thing over and over and expecting a different result.
Currently it is uninstalled. 
I have been trying to install in a second drive, which worked fine before. Is there some corrupted file left after the uninstall? :confused:

[U]Added after problem solved, to save reading to end of thread.
[/U]:
](*,)
PROBLEM After running the wubi installer, the kernel would not load during the first reboot. "Kernel panic- not syncing:VFS:unable to mount root fs on an unknown-block"
\\:D/
SOLVED Others had problems with Kernel panics, and the advice was to defragment the /wubi folder. I did that, the installation finished, and I am writing this in kubuntu.

---

### Post by init1 on 2007-07-07
> **rpalmeri said:**
> After corrupting my files in kubuntu (trying to get two video cards to work- don't ask...) , I uninstalled wubi, and reinstalled it. While it originally worked fine, now whenever I try to boot into ubuntu, I get a message "Kernel panic- not syncing:VFS: Unable to mount root fs on unknown-block (104,1)
I have uninstalled and reinstalled several times, proving the saying that madness is trying the same thing over and over and expecting a different result.
Currently it is uninstalled. 
I have been trying to install in a second drive, which worked fine before. Is there some corrupted file left after the uninstall? :confused:
I have some experience in linux, but be gentle, I'm very close to a  noob.
Looks like a partition/device error. I don't know why this would happen in Wubi. Are you sure you installed it with Wubi?

---

### Post by rpalmeri on 2007-07-07
> **init1 said:**
> Looks like a partition/device error. I don't know why this would happen in Wubi. Are you sure you installed it with Wubi?
 Yep. I've since run chkdsk /f . Now when I install kubuntu with wubi, I get  "Kernel panic- not  syncing: no init found. Try passing init= option to kernel..."

---

### Post by rpalmeri on 2007-07-08
](*,)
 PROBLEM After running the wubi installer, the kernel would not load during the first reboot. "Kernel panic- not syncing:VFS:unable to mount root fs on an unknown-block"
 \\:D/
 SOLVED Others had problems with Kernel panics, and the advice was to defragment the /wubi folder. I did that, the installation finished, and I am writing this in kubuntu.

---

