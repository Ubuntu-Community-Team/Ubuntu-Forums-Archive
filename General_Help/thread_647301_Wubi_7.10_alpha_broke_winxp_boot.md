---
title: "Wubi 7.10 alpha broke winxp boot"
date: 2007-12-22
forum: General Help
---

### Post by BIg2hd on 2007-12-22
Hi

I wanted to try safer way of installing Ubuntu so I d/l wubi 7.10 alpha lol.

Anyways the wubi installing Ubuntu went well, but now every time i choose xp in the dual boot screen I get error "Windows could not start because of a computer disk hardware configuration problem.

Could not read from the selected boot disk. Check boot path and disk hardware.

Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information."

Now i googled that and found Microsoft's official method's to fixing it [here]("http://support.microsoft.com/kb/314477").

I tried all(to be precise Method 1 i didn't do in fear i lose Ubuntu install, 2 and 3 wouldn't go all the way through, and method 4 went all the way through but didn't fix boot.) the methods but no go.

Also for some reason it installed on the same partition as xp(I freed 11 non formated gigs for install) so i'm guessing it has something to with it.

Plz help

---

### Post by Joeb454 on 2007-12-22
Sounds Like Wubi borked the XP install. Although you should've expected something like that to happen.

Did you back up all your important data before hand? Also I think Wubi installs Ubuntu into a folder on XP, I don't know exactly, as I've never used it, I've always dual-booted properly

---

### Post by BIg2hd on 2007-12-22
> **Joeb454 said:**
> Sounds Like Wubi borked the XP install. Although you should've expected something like that to happen.

Did you back up all your important data before hand? Also I think Wubi installs Ubuntu into a folder on XP, I don't know exactly, as I've never used it, I've always dual-booted properly

lol yeeeah thx for that, anyways i did repair install from xp cd and everything seems to be all good. Guess it doesn't matter which way you install ubuntu it's all always gonna mess up my boot, nice to not to have to use GRUB and ability to unistall ubuntu via windows(if in fact it works).

---

### Post by perixx on 2007-12-23
Hy there!

As far as I'm concerned - I had the best experiences with using the native nt-loader to chainload, installed Grub on another partition. Of course you need to use the installation-method 'manual' with Ubuntu then, copy its bootsector-file to XP-partition with the 'dd' command and add an option to the boot.ini file.

perixx

---

### Post by ago on 2007-12-25
More likely that you borked xp boot by hard rebooting your machine... In this case it's sufficient to run chkdsk /r from windows cd

---

