---
title: "Advice from you Multi Distro Booters"
date: 2007-04-11
forum: General Help
---

### Post by Nythain on 2007-04-11
As i mentioned in a different thread i have to wipe my machine clean, wich i dont mind, i like a fresh start every now and then.
Im very familiar with kubuntu, and am upgrading to fesity in all this... but was wanting to get more familiar with other distros (specifically gentoo).
Im looking for info on how to have ubuntu be my main distro install, leaving enough empty partion space for gentoo or whatnot... basically, im confused about two distro's using the same /boot partition, is this possible/recomended.
Next i would like to have two different /homes due to differences in Desktop Environment versions... how do i set two different partitions mounted at the same point... i know its possible because thats what everyone says to do... but i have no idea if its tricky to do, or is it simple since the partions get mounted when the distro boots after grub, so ubuntu would be mounting hda4 at /home while running then unmounting on shutdown, leaving the point free for gentoo to mount hda5 there without conficting with the untouched unmounted hda4.
Then there's /... naturally im gonna need two different partitions mounted there, so im assuming its done the same way as /home.
Finally if both distro's use the same bootloader (grub in this case) then will it play nice with the two of them unlike trying to dual boot windows... or will i need two different instances of the bootload installed in different spots and chainload from the main... example can i keep grub in the default hd0 with ubuntu and have it recognize both ubuntu and gentoo, or will i need to throw another instance somewhere else like hda1 and do this chainloading bit i know nothing about???

---

### Post by indytim on 2007-04-11
Wow, lot's of stuff here in your post.

Background : I'm currently booting Windows 200 Pro, Kubuntu 6.10 (my primary ops), Xubuntu 6.10 and Kubuntu 7.04.  Additionally, I have one partition set up as my master /boot.

ok for your first point (I think it was you first).  If you're coming in "Green" on your ops hd, I'd recommend doing a preconfigure of your partitions with something like GParted Live.  I'd recommend doing:
1.  your first partition at ntfs for Windows and Primarry
2. set up an extended partition for the balance of your hd
3.  set up a swap partition of 2x RAM
4.  ext3 for your primary lx ops
5. ext3 for your primary lx /home
6-n repeat 4&5 as required for each ops system
7.  Carrying multiple ops I'm currently experimenting with a dedicated partition for /boot.

When you do your installs, select the manual partition option and use the appropriate mapping created above.  Note you will also probably have to select the "format" option in the installer for your "/" & "swap" partitions.

Hope this clears the air a bit for you.  Good Luck,

IndyTim

---

### Post by Nythain on 2007-04-11
sweet, helped bunch... glad to hear everything should be a walk in the park... thanks

---

### Post by ygarl on 2007-04-11
Hello!
Multibooter here too...
 
I use Linux Mint, Ubuntu Feisty (or whatever is going) and sometimes I slap on Dyne:Bolic to boot up into if the current version of Ubuntu has problems decent audio recording latency at the time.

Generally, I tend to use seperate physical hard drives but I find if you don't have this option it's best to set one partition up and keep it well alone for your main "work" distro.
Right now for me, this is Mint but it seems to be quite slow and clanky right now - but I'll keep it on until Feisty is stable.

The other partition I keep split into a 1gb partion for Swap, and the rest for the data for the distro (/, /boot and /home). 
I find Ubuntu does a very good job of dealing with changes to Grub so I just reinstall Grub via Ubuntu generally unless it chokes. Then I have to edit the Grub tables manually.

Unfortunately, if editing the Grub tables worries you maybe it is better to wait a but until you have a chance to check the table and become familiar with how to edit it.

Good luck!

---

