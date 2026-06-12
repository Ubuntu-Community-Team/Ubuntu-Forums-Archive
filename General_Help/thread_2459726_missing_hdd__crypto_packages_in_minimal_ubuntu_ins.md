---
title: "missing hdd / crypto packages in minimal ubuntu install?"
date: 2021-03-24
forum: General Help
---

### Post by lenny444 on 2021-03-24
hi,

on 1804 i have a encrypted partition that i access using veracrypt, all i have to do automount partitions in veracrypt and it asks for sudo password then volume password and it is found and mounted automatically.

on 2004 i have a encrypted partition that i access using veracrypt, all i have to do automount partitions in veracrypt and it asks for sudo password then volume password and it does not find the partition.

I am able to point it at sda3 in veracrypt click mount, input sudo password and volume password and it works.

on a 2004 ubuntu minimal install, despite having gnome-disk-utility by default i could not format hdds i had to install gparted to make disks format?

could there be anything missing on a minimal install that is causing this?

i have made sure gparted gpart udisks2 cryptsetup is installed, i thought maybe udisks2 was not installed but it was!

am i missing a package because of a minimal install? is it ubuntu 2004? is it veracrypt?

just a FYI i have apparmor installed if it makes any difference although i uninstalled it and no difference. and i uninstalled snapd (not going to argue about why other than i prefer apt, so lets not get off topic)

SIDE QUESTION is where anything not included in a minimal install that affects stability, security or apps?

thank you

---

### Post by TheFu on 2021-03-24
I've never used veracrypt, but if you install the **cryptsetup** package, then all the LUKS dependencies will get pulled in.  I have no clue what udisk2 is. Sorry. Never used it.

2004 was a long time ago. I don't think veracrypt existed then. ;)

I've not needed to touch apparmor for encrypted setups either.  The only times I needed to touch apparmor was with snaps - I'm not a fan either - at least not with some of the mandated decisions with no way for local overrides.  Ubuntu computers and servers are not cell phones. I'm not against the goals for snaps, just a few of the implementation details which have made them useless for many corporate environments.

To my knowledge, there are 2 people using veracrypt on Linux. Until 2021, I'd never heard of any.  I've been using dm-crypt w/ LUKS for about 6 yrs, maybe longer. It is integrated into the DE and file manager for Mate. I don't know about other DEs, sorry.  About once every other year, does that file manager integration matter to me. The rest of the time, it is only at boot time when I notice LUKS - the system won't boot until I unlock the partition with my Yubikey(s).

---

