---
title: "GRUB Loader and Hard Drive Boot Priority"
date: 2008-06-18
forum: General Help
---

### Post by Zuwxiv on 2008-06-18
**Nevermind, I found my answer.**
Hey guys, this is my first post here. I've always come here for help though, and I hope you'll be as useful for my question as you've been for others!

Anyway, I've messed around with several linux distros (SUSE, Ubuntu, Kubuntu...) and most recently I've been using Linux Mint, which is a variant of Ubuntu. I just have a question about the GRUB loader...

I've set boot priority to my first (and largest) hard drive, first. It's an XP drive, through and through. And yet, when I install linux on the third priority hard drive, and put it on partition 2, the GRUB loader comes up. I'm going to edit it to make XP the default one (I do use it most, although maybe that'll change soon. I just like my games too much...), but here's my main question:

Why is it that the GRUB loader will always come up; shouldn't it boot from the first hard drive and go right into XP? Even if I want to start XP, it will either take me paying more attention to boot or (if I make it default) add 10 seconds to my boot time. If I do a fixmbr on my windows partition, can I still start the linux partition on the other drive?

Thanks in advance guys, I really like linux but I'm just not quite ready to make it my primary OS.



Edit: Looking around in the menu.lst file, I found a "default grub root device" option ("groot") which I could set to the XP drive. How would this effect it? Would this fix it (autobooting from XP when the computer starts up) or would it make the linux partition not reachable?

**Double Edit**: I'm retarded, I just checked the BIOS and found that it actually wasn't set to my boot priority. Duh. Anyway, my question was answered quickly. There's like an aura around this place. :P

---

