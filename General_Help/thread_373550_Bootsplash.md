---
title: "Bootsplash"
date: 2007-03-01
forum: General Help
---

### Post by energiya on 2007-03-01
Hi,
I'm trying to change my bootspash theme. If I make a mistake in the theme's config, will my PC boot? I don't need to see anything just to boot and fix the problem (if any).

---

### Post by dannyboy79 on 2007-03-01
i am not sure what will happen, but I would suspect it would boot? here is a guide for changing your boot splash image. 

[http://ubuntuforums.org/showthread.php?t=11478](http://ubuntuforums.org/showthread.php?t=11478)

you will always be able to get at your system files and fix anything using a live cd, so don't be afraid to play around. also, always make a backup of any file you change, this way, if something doesn't work, you can just overwrite the new modfied file that doesnt work with the one you backed up. good luck.

actually here, i just found how you can fix a bad boot splash mess up, you would have to chroot into your system from the live cd or just boot to system recovery option from grub but I doubt that your computer would fail just because it can't find the splash image.
[http://parker1.co.uk/satanic/add-ons/gnome-splash-screen/](http://parker1.co.uk/satanic/add-ons/gnome-splash-screen/)

---

### Post by energiya on 2007-03-01
Thanks for the answer! Even thow I now use a Slackware based distro, I think I can still mount my / using the Ubuntu live cd.

---

### Post by dannyboy79 on 2007-03-01
ok, not sure why you are informing me of this? if it's because I think, than I would like to point out that you can't just mount / and run that command I linked to, you need to be chrooted into  your install so that it takes effect within your gconf for ubuntu. at least I believe that's the case.

---

