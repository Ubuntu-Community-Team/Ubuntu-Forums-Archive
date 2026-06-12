---
title: "Rresizing /boot"
date: 2022-03-01
forum: General Help
---

### Post by pavloos on 2022-03-01
Hi,

I was fighting with your help on this [issue>>>]("https://ubuntuforums.org/showthread.php?t=2472404"). There was a problem with low space on /boot. Now I am considering when it would be safer to add some more free space to it:
1. In a few months when I would be clean installing 22.04 LTS
2. Now.

If now, then is it really as simple as [this answer>>>]("https://askubuntu.com/questions/280211/how-do-i-resize-my-boot-partition") suggests. Or I may encounter some problems as it is 8 years old? Also /boot is encrypted.

> 2. [COLOR=#232629][FONT=inherit]To grow boot you first need to shrink another partition so you have free space. I would suggest using the GParted partition editor on a live Ubuntu USB to do this. First decrease the size of [/FONT][/COLOR]/[COLOR=#232629][FONT=inherit] or [/FONT][/COLOR]/home [COLOR=#232629][FONT=inherit]depending on your setup. Then increase the size of [/FONT][/COLOR]/boot[COLOR=#232629][FONT=inherit].[/FONT][/COLOR]

Best,
p

---

### Post by Impavidus on 2022-03-01
I already replied to your other thread before I read this one.

No, it's not that easy to increase the /boot partition in size. It's doable, I guess, but you first have to use LVM tools to shrink the other partitions, as gparted can't do that with lvm. We have some users here who know everything about lvm, but I'm not one of them. It will be simpler to just deal with this tight /boot partition for a few months, until you install 22.04. You can remove the old kernels yourself when the need arises.

---

### Post by TheFu on 2022-03-01
I would wait.  

As MAFoElffen says, when we use LVM, we really are dealing with a Russian doll-inside-a-doll-inside-a-doll-inside-a-doll-inside-a-doll issue.  

Add in encryption and partitioning and we have 2 more doll-layers and will end up having to do a reinstall. 

May as well wait for a fresh install later and hope that the encrypted installation options pick more reasonable partition sizes. In June when you do install 22.04, be certain to wipe the partition table first, so the disk is truly empty, as far as the installer knows. Obviously, you'll need to save off data and other stuff you don't want to lose to other storage first ... but your normal file-based backups should handle that already.

The LUKS encryption partitioning included in the installer leaves much to desire, but there isn't much we can do about it and still have installation be 15 minutes.  The manual install with encrypted OS is complex enough that I've been scared away.  The first thing I do post-install of an encrypted system is resize the "root" LV down to a reasonable size (say 35G), add an LV for var and home each, sized for the next few months only, and ensure the swap LV is 4.1G in size.  That usually leaves 400G of unallocated storage in the VG which is already encrypted and just waiting to be added to the LVs as needed - in about 5 seconds - while the system keeps running. It is a beautiful thing. Truly.

If I don't resize the 'root' LV ASAP post-install, it just becomes a hassle and the risk of data loss increases, so do it ASAP post-install. This lvreduce command has to be done after booting with alternate media - I'd just use the same Ubuntu Install flash drive, but in "Try Ubuntu" mode.

Maybe we'll get lucky and the next installer will support customized LVM setups for encrypted storage that are easier? There's always hope.

---

### Post by pavloos on 2022-03-05
Thank you both. I'll wait

---

