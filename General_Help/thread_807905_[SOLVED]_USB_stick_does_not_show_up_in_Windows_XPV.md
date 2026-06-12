---
title: "[SOLVED] USB stick does not show up in Windows XP/Vista"
date: 2008-05-26
forum: General Help
---

### Post by Beefeater on 2008-05-26
G'day,

I got a 1 GB USB stick with two partitions.

sdc1 - 850 MB truecrypt
scc2 - 150 MB fat32

My problem is what the title says, it doesn't show up in Windows XP/Vista.
"Drive not formatted. Would you like to format ..." or something like that.

What I will try is to erase the entire stick and start over from the beginning having the fat32 partition as sdc1.

But will it make a difference? I dunno.

Gotta run out in the sun now, maybe someone can shed some light on this issue?

Cheers

---

### Post by drsaamah on 2008-05-26
When you remove the drive from a linux machine, do you safely remove it?  In other words, you should right click the mounted drive icon on the desktop and select "Eject".  I never understood why this was such a big deal until I started using Linux and then I learned that if a drive isn't safely removed from Linux it won't work on a Windows platform and vice-versa.  the truecrypt partition may also be the problem, but I can't say I have had any hands on experience to comment from.  Good luck!

---

### Post by Beefeater on 2008-05-26
> **drsaamah said:**
> When you remove the drive from a linux machine, do you safely remove it?  In other words, you should right click the mounted drive icon on the desktop and select "Eject".  I never understood why this was such a big deal until I started using Linux and then I learned that if a drive isn't safely removed from Linux it won't work on a Windows platform and vice-versa.  the truecrypt partition may also be the problem, but I can't say I have had any hands on experience to comment from.  Good luck!

Yes I remove it safely.

But I solved it by formatting it again with fat32 on sdc1 and then truecrypt on scd2.

Have a good day!

---

