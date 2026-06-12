---
title: "just installed ubuntu via wubi what now"
date: 2008-01-05
forum: General Help
---

### Post by exneo002 on 2008-01-05
just plopped my ubuntu disc in in a windows session and installed via wubi what now it installs but loads via my live cd I'm planning on doing this with ubuntu 7.10 and ubuntu ultimate edition 1.6 so plz give me generic instructions

---

### Post by wolfen69 on 2008-01-05
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by exneo002 on 2008-01-05
that didn't solve my question I have to know If it will work by installing wubi reboot into live cd and install via the standard installer

---

### Post by wolfen69 on 2008-01-05
yes.

---

### Post by exneo002 on 2008-01-05
thax by the way how do I get the caption to say somthing other than 5 cups ubuntu

---

### Post by exneo002 on 2008-01-05
that didn't work how do I put the iso file in the same directory as the wubi so it will detect my ubuntu ultimate edition 1.6 and install that

---

### Post by Sef on 2008-01-05
Moved to wubi forum.

> thax by the way how do I get the caption to say somthing other than 5 cups ubuntu

They randomly change from time to time.

---

### Post by ago on 2008-01-07
exneo002 what do you want to do exactly?

---

### Post by mikedep333 on 2008-01-10
> **exneo002 said:**
> just plopped my ubuntu disc in in a windows session and installed via wubi what now it installs but loads via my live cd I'm planning on doing this with ubuntu 7.10 and ubuntu ultimate edition 1.6 so plz give me generic instructions

[QUOTE=exneo002]that didn't solve my question I have to know If it will work by installing wubi reboot into live cd and install via the standard installer[/QUOTE]

I think what he is asking here is how come he can not get into his wubi install when he has the ubuntu desktop/live CD in his drive. 

Exneo, to run your Wubi install of ubuntu, just remove the desktop/live CD. It is not needed at all to run wubi.

I believe he also would like to know how to get Ubuntu Ultimate Edition installed.

Exneo, you can install regular Ubuntu 7.10 either to its own partition (the normal way) or through wubi. You cannot install Ubuntu Ultimate Edition through wubi (to the best of my knowledge,) you have to install it to its own partition from the live CD. What you may want to do to avoid too many partitions, is install regular Ubuntu 7.10 through wubi (I believe you have already done this) and then install Ubuntu Ultimate Edition as it is normally installed to its own partition. This normal install of ultimate edition is accomplished using its live/desktop CD. First, check your hard drive in Windows (running chkdsk /f from a command prompt as administrator, or right clicking on the disk under my computer.) Then run the Ubuntu Ultimate Edition Installer from the live/desktop CD and just let it do the automatic partitioning (let it resize your windows partition that contains wubi, but by all means do not proceed if it proposes deleting any partition.) After this your regular wubi install will still be available.

Once this is done, eject the any live CDs and use your system. You should first have the option of booting into Ubuntu Ultimate or into (the bootloader of) Windows. If you select windows (its bootloader), you will then have the option of booting into Wubi Ubuntu or Windows.

---

