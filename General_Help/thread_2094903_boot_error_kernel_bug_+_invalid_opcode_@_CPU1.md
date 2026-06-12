---
title: "boot error: kernel bug + invalid opcode @ CPU1"
date: 2012-12-15
forum: General Help
---

### Post by Goupit on 2012-12-15
Hello everyone. Sorry if this thread is not in the right place. I have a dual boot ACER laptop with Ubuntu 11.10 and W7. The graphics card is an ati mobility radeon.
Some times, only when i choose ubuntu to load in the grub, after 2 or 3 seconds i get this error:

[IMG]http://i1265.photobucket.com/albums/jj518/0gap/kernel_bug_inv_op_codeCPU1_zps5d182cc1.jpg[/IMG]

I reset the system and all is well. I boot into Ubuntu just fine.
Has anyone faced something like it?

---

### Post by Rexilion on 2012-12-15
If it happens every once in a while, then that bug is called a race condition.

But, maybe there is a pattern. Does is only happen if you reboot W7 and then go into Ubuntu? Maybe W7 leaves stuff behind on the VGA card which causes an exception in the Linux kernel.

---

### Post by Goupit on 2012-12-15
> **Rexilion said:**
> ...Does is only happen if you reboot W7 and then go into Ubuntu? ...

No, actually that is not the case. For example I was working all day yesterday in Ubuntu and today when booted in again this occured. I took the opportunity and posted it after long time that this problem occures. And i don't think a specific program or process would cause this. And writing down everything i've done during the day, plus waiting for this to happen again is impossible. Even though i'm curious to observe if something like it, could be the reason behind this error.

What i was wondering was, i see in the /boot folder files that indicate past releases back to 3.0.0.12, could this cause any problems?

I had problems with the graphics card(did alchemies for switchable graphics proposed here and there, installed-uninstalled ati drivers because they didn't work) but that seems to me it would cause a problem that would insist, or am i wrong there? For example when i used to install any drivers for the ati, ubuntu didn't even start.
So if this has to do with the drivers what can be done to "clean-reset" the whole graphics drivers-system, if i may use such words? Can something like it be done? Or is it even worth the trouble, considering i am looking forward in a couple of months to upgrade to 12.10?

---

### Post by Rexilion on 2012-12-16
Everything should be reset if you turn of the power and leave the computer like that for a while.

It is a bug, albeit a minor one. I think that if you can live with this and will upgrade to 12.10 in a few months then I would sit it out.

Especially since a lot has been done on Radeon cards when one looks at the drivers. It is a really good possibility your issue will go away after an upgrade.

---

### Post by Goupit on 2012-12-16
I think I'll stay put. Rexilion thanks for your advise. I'll wait a few days before i close the thread. Maybe someone has an idea on this glitch. It was more out of curiosity that i opened this thread.

---

