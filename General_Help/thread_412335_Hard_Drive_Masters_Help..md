---
title: "Hard Drive: Masters? Help."
date: 2007-04-18
forum: General Help
---

### Post by InfamousMyzt on 2007-04-18
I have two hard drives, and i don't want to do a slave setup. Is it possible that putting ubuntu 6.10 on a seperate hard drive could interfere with windows xp on the first one? I installed ubuntu on the other and windows started crashing and i had to reformat this winxp drive about 7 times before it was willing to work again. Any know problems with swapping masters like this? I have a seagate 120gb for windows and a maxtor 80 gb for linux. Pheonix BIOS.

---

### Post by BoneKracker on 2007-04-18
> **InfamousMyzt said:**
> I have two hard drives, and i don't want to do a slave setup. Is it possible that putting ubuntu 6.10 on a seperate hard drive could interfere with windows xp on the first one? I installed ubuntu on the other and windows started crashing and i had to reformat this winxp drive about 7 times before it was willing to work again. Any know problems with swapping masters like this? I have a seagate 120gb for windows and a maxtor 80 gb for linux. Pheonix BIOS.

I don't know what you mean by a "slave setup".  If you put two drives on an IDE controller, one is the "master" and the other the "slave".  That's just the way it is.  About the only thing it means is that the BIOS (or firmware, depending on what kind of computer you have) will assume that the "master" is the boot-disk unless you tell the BIOS differently.

Yes it is possible that putting Ubuntu on a separate drive could interfere with what's on the first one.  It's also possible to poke yourself in the eye with a pencil.  Normally, putting Ubuntu on a second drive will not interfere with what's on the first one except as follows:

a) The ubuntu installer will (by default) replace the Master Boot Record (MBR) on the system's boot disk (i.e. the "master" disk) with one that points to the bootloader files that Ubuntu installs.  These bootloader files are, in your case, on the second drive, and they are what is used to put the menu up on the screen so you can choose which system to boot into.  If you then remove the whole ubuntu install, or b0rk your bootloader files, you will have difficulty booting.  Then you have to either reinstall the bootloader or restore the original DOS MBR that points to the Windows bootloader files instead.  This is not really "normal" but it does happen (and ER doctors remove pencil lead from faces every year too).

b) By default, the Ubuntu installer will set up mount points for any existing Windows partitions, enabling you to get access to your Windows files from Linux.  Even though this is (I believe) only read access, this is a bad idea because it gets people started thinking about having read-write access, and soon they are monkeying around with their NTFS partitions from within Linux.  The software that enables read-write access to NTFS partitions from within Linux is just now nearing maturity and is not without problems.  So this is a second way that a Linux installation can in fact mess up a Windows installation.  With all the "cross-over" users these days, I would expect NTFS filesystem utilities to mature rapidly and this problem to partly go away.  There will still be the people who delete files that were "hidden" by Windows because they don't know what they are and what they do.  And doctors will continue to remove vegetables and household implements from body cavities.

Case (a) above has nothing to do with your Windows software crashing.  Case (b) could conceivably have caused some damage that would cause Windows to crash, but that would be your own fault -- a self-inflicted wound, so to speak.  Now with that background established, I am going to try to interpret your question:

You would like to install Ubuntu in such a way that it does not interfere at all with your Windows installation.

1.  The best way to do this is indeed to put it on a separate disk.  Then during installation, when it gets to the part where you are partitioning the disks, where it has your NTFS partition(s), click "Use as:" and choose "Do not use:".  That takes care of case (b), for the most part.  

2.  If you really want to isolate it fully, although there is really no risk caused by case (a), you can have Ubuntu put its bootloader's MBR on the slave disk instead of the master, and then tell the BIOS that the other disk is now the boot disk.  Just make sure that you also have the bootloader set up to allow you to choose to boot Windows (you want an entry that "chainloads" the Windows bootloader).  That takes care of (a).  I don't recall if this option is given to you by the normal Ubuntu installer or if you have to use the alternate install cd (or do it manually).  Then, for the duration that you want to be "dual-booting", you have your "slave" disk be the system's boot disk, and it brings up the linux boot menu, and that menu gives you the option to call the Windows bootloader.  The benefit of this approach is that if you were to completely mess up your Linux system or say, rip the second disk completely out of the system, you merely switch the bios back to booting the master disk and you're in business with a regular old crappy Windows box the way you started.  One thing NOT to do is change which disk is the master and which is the slave once you have a system installed on either (not by physically swapping them, not by changing cable connections, and not by changing jumper switches).  Only change by the BIOS (or firmware) or you will confuse both systems.

---

### Post by InfamousMyzt on 2007-04-18
I meant that I will be using 2 master hd's and I will switch them out depending which I want to use.

---

### Post by BoneKracker on 2007-04-18
Aha!

That is fine, as long as you actually REMOVE or DISCONNECT the other disk (and don't try to have it be the "slave").  That goes for when you are installing as well as later when you want to run it.

If that's what you're planning, then no, there is no way I know of that one OS could interfere with the other.

[Edit]:

And this is embarrassing but funny, so I'll mention it.  I thought you were asking for help from the "Hardrive Masters", like the "Gurus of Hard-drive Land" or something.

---

