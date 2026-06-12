---
title: "How can I install XP without messing up ubuntu??/"
date: 2007-12-05
forum: General Help
---

### Post by jrharvey on 2007-12-05
My computer came with Vista and I setup a dual boot with ubuntu on it and have used that setup fine for about 5 months. I am now FED UP with vista and want to go back to XP with dual boot. Vista has given me nothing but problems with my architecture programs. The problem is that I know windows will overwrite grub if i install it over top of vista. Right now GRUB is managing my 2 OS's so what can i do to be able to dual boot when installing XP. Is the windows boot loader worse or better? Will it even let me choose ubuntu? Can I still use GRUB?

---

### Post by jrharvey on 2007-12-05
Reinstalling Ubuntu is not an option right now. I have waaaaaay too much work involved.

---

### Post by logos34 on 2007-12-05
Use this guide to restore grub after you install xp:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jrharvey on 2007-12-05
So it is true that if I install windows XP I will not be able to boot into Ubuntu? I will try this and thank you.

---

### Post by logos34 on 2007-12-05
yeah, windows install overwrites the mbr with its own bootloader (ntldr), there's no way to stop it

---

### Post by el escocés on 2007-12-05
Have a supergrub CD handy to boot back into Ubuntu after the window install [http://forjamari.linex.org/frs/?group_id=61&release_id=499](http://forjamari.linex.org/frs/?group_id=61&release_id=499) then reinstall grub.

---

### Post by Sef on 2007-12-05
> Have a supergrub CD handy to boot back into Ubuntu after the window install [http://forjamari.linex.org/frs/?grou...release_id=499](http://forjamari.linex.org/frs/?grou...release_id=499) then reinstall grub.

Super Grub is great.   Here's a [tutorial]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") on it.

---

