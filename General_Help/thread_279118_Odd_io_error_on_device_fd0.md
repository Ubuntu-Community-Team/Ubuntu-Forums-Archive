---
title: "Odd i/o error on device fd0"
date: 2006-10-17
forum: General Help
---

### Post by RayH on 2006-10-17
Hi all,

Odd error which I didn't find in a quick search on the forum:

I am getting a gnome desktop crash if I'm in Hotmail and writing a long email, the desktop just shuts down to tty1 with a buffer i/o error on device fd0, and then the desktop restarts itself automatically (almost as if I've done a control-alt-backspace).  Any ideas?  I'm running an AMD 2600 with 2.6.15-27-k7

Thanks!

---

### Post by RayH on 2006-10-18
Well I researched a little by myself, and at least I'm a bit closer.  I linked the fd0 (floppy errors) to vmware by watching tty0 during the launch of a vm.  So I disabled the floppy on the vm, and the errors have stopped for now.  I don't have a reason to use the floppy at all so no big deal there, but eventually I'll troubleshoot it.  I'm guessing that the logs became full from all the fd0 errors and would crash the gnome desktop, that's what I'm guessing by my limited knowledge, I just don't know what log it writes to.  

I know that noone responded, but I thought I'd post up a semi-fix anyway in case anyone else came across this problem.

---

