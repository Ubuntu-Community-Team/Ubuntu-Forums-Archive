---
title: "Pre-installation question"
date: 2007-05-28
forum: General Help
---

### Post by leaston on 2007-05-28
Hi,

This is my first post, so please be gentle with me :D

I would really like to install Wubi on my main PC as it's the only one left without Linux. It currently runs XP only. As this PC is the one I can't afford to break due to my needing Windows for the next few months, I'm a little concerned about it.

Considering the way Wubi installs Ubuntu as a single file, much like VMWare, then it's no big deal in that respect. My worry is about not being able to boot to Windows if the mbr is damaged in some way. If that does happen, I take it I can simply overwrite grub with "fdisk /mbr" to get the default Windows loader back? I have done this before with other PC's when removing a Linux distro, so wondered if it would be a good fix in this case?

I'm not trying to be cynical, but after working in IT for many years, I have learned the hard way that if it can go wrong, it will!!! ;)

Cheers,
Leaston

---

### Post by ago on 2007-05-28
The mbr is not touched. Consider trying the latest minefield (96-46)

---

