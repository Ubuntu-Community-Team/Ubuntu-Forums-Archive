---
title: "Please Help, Extreme Boot Issue"
date: 2008-05-14
forum: General Help
---

### Post by Aesir09 on 2008-05-14
ok, i was dual booting vista+8.04 and everything was working, was going to temp uninstall ubuntu, so in vista, i deleted partition until it was "unallocated space"

and then i merged it into the windows partition.

i get GRUB error 22.

i need to do a speech tommorrow for school and am showing how to install something, i need to get my laptop working.


PLEASE HELP!!!!

NVM I CAN BOOT INTO CD BUT what command do i use?

---

### Post by NightwishFan on 2008-05-14
Download a super grub disk and boot with that for now.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by shifty_powers on 2008-05-14
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3](https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3)

and also, try running your windows set up cd, and go into the recovery console and try the fix mbr tool (master boot record).

also check the boot options in your bios and make sure that it is set to boot from the cd BEFORE the hd ;)

---

### Post by Aesir09 on 2008-05-14
ok well do i just write everything from supergrub (folders) to a cd?

and im running in a vista cmd prompt right now off my recovery, i need some kinda fixmbr command.

---

### Post by NightwishFan on 2008-05-14
If you have a vista cd run fixmbr from there i am not sure if you can elsewhere. For the supergrub burn the .iso to a cd, (not a data cd as an image).

---

### Post by Aesir09 on 2008-05-14
i seriously love me, i can do anything

im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome
im awesome


if you haven't guessed yet i fixed it.

its
```

bootrec/FixMbr
```

for vista

---

### Post by NightwishFan on 2008-05-14
:popcorn: Good job sir.

---

### Post by Aesir09 on 2008-05-14
btw nightwish owns!

---

