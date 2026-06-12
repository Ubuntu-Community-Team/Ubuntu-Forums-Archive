---
title: "Total Beginner help please."
date: 2007-09-29
forum: General Help
---

### Post by papasworld on 2007-09-29
Hi, complete and utter total beginner here. I really like the look (and idea) of Ubuntu but I'm not having much success.

I'm using Wubi to install Ubuntu 7.04 on my XP home machine. It installs the dual-boot thing and I can select Ubuntu for the initial install (as opposed to booting into XP). However, it gets as far as detecting hardware settings, goes to a blue screen and does nothing else. There's nothing on screen to tell me what it's doing and or what's gone wrong. I have to reboot my PC and if I select Ubuntu again, it tells me that something has gone wrong with the installation and will have to reboot (which it does). The only thing I can do now is to boot into XP and remove the install and start again. I've left it for half an hour on the blue screen in the (vain) hope that something is happening.

Has anyone got any ideas?

Thanks

Paps

PS btw, I first posted this on the Absolute Beginner Talk forum but was pointed to here instead.  I thought that Wubi had done it's job at this point but maybe I'm wrong?

---

### Post by clive_pearce on 2007-09-29
I'm a newbie as well. I would go to windows & uninstall wubi from the add/remove programs. It should ask you if you want to save some files, including the iso, that way, you shouldn't have to download the iso again.

Reboot to windows to make sure that is still ok. Then try the install again. 
:)

---

### Post by papasworld on 2007-09-29
Thanks Clive

Yes, unfortunately I've tried uninstalling and re-installing several times now all to no avail.

Have you managed to do this ok?

Cheers

P

---

### Post by open2linux on 2007-09-29
Defrag Windows before reinstalling.
This sometimes helps.
Good luck!

---

### Post by clive_pearce on 2007-09-29
Hi papasworld,

  I've installed & uninstalled wubi on different machines with no problems. If you say it gets as far as detecting hardware, perhaps thats the problem.

Try downloading a Live cd & running that to see if there are any hardware problems.

---

### Post by papasworld on 2007-09-29
Hi Clive

I've tried the Live CD previously and it worked ok bar a couple of problems (no sound / internet or network) - but didn't know enough to fix them. (probably simple things!)

I'm currently defragging so I'll give it another go after that.

Thanks for your help.

P

---

### Post by HOF on 2007-09-30
papasworld

I have the same problem, being I encounter the blue screen (of death?) whenever I try to install with Wubi, and I don't know how to get past it.

Windows Defrag and install did nothing to aid me.

Also, the blue screen appears briefly after the formatting of the virtual disk, and then something about hardware appears with a loading bar whichis then replaced by the blue screen again.
I have run the LiveCD before and have encountered no problems at all.

---

### Post by papasworld on 2007-09-30
Hi Hof

Sorry to say but I never managed to get round the problem.  I've decided to go down the partition route after all but I'd still rather use Wubi if I can.  I'm wanting to solve my network problem before I do the full install though - partitioning terrifies me.

---

### Post by clive_pearce on 2007-09-30
Hi papasworld, 

as I said I'm a newbie, blue screen of death could be a hardware problem. I'd run chkdsk, perhaps sfc /scannow, memtest for the memory, all from windows.

If you still have problems with wubi & want to go down the partitioning route, I'd partition the disk before installing ubuntu.
 If you create a separate partition of for example Ext3, using partition magic or gparted. Run the ubuntu live cd, if you run the install from there it will show up the Ext3 partition & ask if you want to install to that partition , the wizard should select the swap file size etc for you.

If you are still unsure, you could try installing to an external usb drive. (if you have one)

---

### Post by ago on 2007-10-01
De a fresh install

If it jams press alt+f4

and post here the latest lines (or any error message).

PS if you have USB devices try to disconnect them

---

### Post by HOF on 2007-10-04
> **ago said:**
> De a fresh install

If it jams press alt+f4

and post here the latest lines (or any error message).

PS if you have USB devices try to disconnect them

I unplugged everything from the pc, including my wireless adapter, and I breezed through the install :)

I advise you try that too papasworld

---

