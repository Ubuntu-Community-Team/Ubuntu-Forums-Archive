---
title: "Help creating virtual machine using Boxes"
date: 2018-04-22
forum: General Help
---

### Post by tjsilver on 2018-04-22
Hello!

I'm using Ubuntu 16.04 and I'm trying to create a VM using Boxes.  On this VM I want to install Ubuntu 16.04 for me to practice on (and not care if I make OS-knackering errors!).  But when I try to open the VM all I get is 'Failed to start...' but no explanation as to why!

Advice please.

Tim

---

### Post by kerry_s on 2018-04-22
that means it's broken again.

do yourself a favor & just use virtualbox. it breaks the least & it's the most commonly used if your ever looking for help.

you can also opt for virtual machine manager(vmm) if your looking for something as simple as boxes.

---

### Post by tjsilver on 2018-04-23
Thought that might be the case. I'm still naive enough to imagine that if it's in 'Ubuntu Software' it will install and work OK - not so!

---

### Post by kerry_s on 2018-04-23
i love gnome boxes for it's simplicity, but like i said it breaks all the time.
i'm using virtual machine manager, it's in the software center. it's the next easiest. 
virtualbox is okay if you like to tweak settings. i just try other distros/versions.
[ATTACH=CONFIG]279416[/ATTACH][ATTACH=CONFIG]279417[/ATTACH]

---

### Post by PaulW2U on 2018-04-23
> **tjsilver said:**
> I'm using Ubuntu 16.04 and I'm trying to create a VM using Boxes.  On this VM I want to install Ubuntu 16.04 for me to practice on (and not care if I make OS-knackering errors!).  But when I try to open the VM all I get is 'Failed to start...' but no explanation as to why!
I'm certainly no expert in these matters but I've also failed to get Boxes working (in the latest development release) and have been left wondering what I have been doing wrong.
> **kerry_s said:**
> i love gnome boxes for it's simplicity, but like i said it breaks all the time.
It seems it's also broken in Ubuntu 18.04 which is due to be released on Thursday. See bug report: [GNOME boxes fails to start virtual os]("https://bugs.launchpad.net/ubuntu/+source/gnome-boxes/+bug/1762205").

Since last evening I've created several VMs by installing **Virtualbox** which can be found in the Ubuntu repositories. I'm only a beginner with VMs but at least I managed to get Virtualbox working with very little effort. Virtualbox might be a little more complicated to set up but it does work.

---

