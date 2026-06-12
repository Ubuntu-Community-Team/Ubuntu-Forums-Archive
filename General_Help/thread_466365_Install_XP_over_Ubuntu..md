---
title: "Install XP over Ubuntu."
date: 2007-06-06
forum: General Help
---

### Post by loathsome on 2007-06-06
Hi there folks,

What's the easiest way to install XP when I only have Ubuntu and not still be able to dual boot with GRUB?

Vice versa GRUB configures everything automatically, but I don't think that's the case if I already have Ubuntu.

Thanks.

---

### Post by tgm4883 on 2007-06-06
You want to install XP and get rid of ubuntu?  If thats the case, pop the XP cd in, when it boots into the XP cd install, delete all the partitions (or keep some if you want) and go through the rest of the XP install

---

### Post by loathsome on 2007-06-06
Nono, I want to install XP on a 5GB partition for some games and **dual boot**.

Why the heck would I ever want to remove Ubuntu? ;)

---

### Post by tgm4883 on 2007-06-06
> **loathsome said:**
> Nono, I want to install XP on a 5GB partition for some games and **dual boot**.

Why the heck would I ever want to remove Ubuntu? ;)

Ah.  Didn't know, but some people are crazy.

---

### Post by floke on 2007-06-06
AFAIK it's VERY difficult to install XP after ubuntu. Probably quicker to back up, install XP on whole drive, and reinstall ubuntu after.

---

### Post by logos34 on 2007-06-06
> **loathsome said:**
> Nono, I want to install XP on a 5GB partition for some games and **dual boot**.

Why the heck would I ever want to remove Ubuntu? ;)

I'd give more like 8GB...I know, I've tried...Unless you install almost no apps and maybe disable hibernation file (~500mb).  It'll be a tight squeeze.
And you have to leave 15% free space in order to run defrag.

Also, windows must be the FIRST partition...You don't need the whole disk but it must be at the front.  Otherwise, install will go fine up to copying files into 'Windows' folder, but then it wants to reboot and, bang, blue error screen.

---

### Post by hessiess on 2007-06-06
if you want if for games give it 20 gig. outherwise you will only be able to have 1 installed at any 1 time!

---

### Post by Crafty Kisses on 2007-06-06
> **Steve.K said:**
> AFAIK it's VERY difficult to install XP after ubuntu. Probably quicker to back up, install XP on whole drive, and reinstall ubuntu after.

That's probably the best way.

---

### Post by logos34 on 2007-06-07
>  Originally Posted by Steve.K  View Post
*AFAIK it's VERY difficult to install XP after ubuntu. Probably quicker to back up, install XP on whole drive, and reinstall ubuntu after.*

That's probably the best way.

Just to set the record straight, it is not true that it's 'VERY difficult to install XP after ubuntu.'  I've done it several times without a hitch, XP on hda1 and linux on hda4.  The only thing is, that windows install blows away grub on the mbr and replaces it with ntldr, which is easily reversed by reinstalling grub.  Also, windows insists on being the FIRST partition on the disk and also must be fooled into thinking that it's on the first drive in the bios hard disk boot order (in cases where you are booting to windows via the grub menu on a different disk).

---

### Post by loathsome on 2007-06-07
Aw, crap.

Seems like too much work for me :lolflag:
Oh well, I'll just run XP in WMware, I don't play too many games anyway.

Thanks

---

### Post by Secession on 2007-06-13
I've had a fair bit of success dual booting using bootpart to make a line in BOOT.INI that points at a Linux installation.  It might help...

---

