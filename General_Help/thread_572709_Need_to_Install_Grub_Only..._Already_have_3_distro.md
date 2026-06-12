---
title: "Need to Install Grub Only... Already have 3 distros"
date: 2007-10-10
forum: General Help
---

### Post by RandomUsr on 2007-10-10
I just want to install GRUB From the Ubuntu, Feisty CD. Could someone give me a few pointers?  

Thanks in Advance!

---

### Post by bodhi.zazen on 2007-10-10
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Yea, it is written for restring grub after windows, but same basic procedure.

---

### Post by RandomUsr on 2007-10-10
Ok i just want to add Grub... I remembered that when Grub was in use that it actually mentioned loading Grub Stage 1.5 but the articale only talk about loading stage 1.... What's going on there?

---

### Post by bodhi.zazen on 2007-10-10
I assume you are asking about the command to 

find /boot/stage1

You are just trying to identify your boot partition is all.

---

### Post by RandomUsr on 2007-10-10
Exactly. So i just need to boot the liveCD grub , run that command and it will recognize all 3 linux distro's plus XP and Vista. No manual stuff?

---

### Post by bodhi.zazen on 2007-10-10
> **RandomUsr said:**
> Exactly. So i just need to boot the liveCD grub , run that command and it will recognize all 3 linux distro's plus XP and Vista. No manual stuff?

I do not know if I would go that far, you may need to manually configure grub to boot your windows partitions. Do you know how to do that if needed ?

---

### Post by RandomUsr on 2007-10-11
I could prolly figure it out after the third or fourth time I delete my Windows partitions with all of my data.... help would be nice

---

### Post by bodhi.zazen on 2007-10-11
you will not wipe you windows installs by installing grub.

Select one of your Linux partitions to be the master, or boot partition. Install grub, see if it works.

If not we will need some further information ...

Partitions, and the relevant sections of /boot/grub/menu.lst from your boot partition.

---

### Post by RandomUsr on 2007-10-11
Ok I'll do that and let you know what happens.

---

