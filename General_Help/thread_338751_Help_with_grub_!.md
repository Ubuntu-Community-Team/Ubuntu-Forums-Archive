---
title: "Help with grub !"
date: 2007-01-14
forum: General Help
---

### Post by hoopscoop on 2007-01-14
Hello, all
After an afternoon filled with gparted and a drive with errors ](*,) , I finally was able to get ubuntu installed. (Dual Boot with xp pro sp2)
After a few reboots, I had a problem, Grub would barely load, then my system would crash, re-start and start an endless cycle ;(

I had to eventually boot with the XP then chkdsk /P,
tried to restart no luck.

Lastly I booted with the windows cd and had to fixmbr !

Well, I didnt have the ubuntu boot info saved to a disk, so
now I have ubuntu installed, but no way to boot to it ;(

Any way of adding it to my startup menu, without having to reinstall all over again  ?


Thanks,
Glenn

---

### Post by Rippey on 2007-01-15
boot from a live cd,
open a console,
type "sudo grub-install"
you're done, reboot and grub should load.

---

### Post by hoopscoop on 2007-01-16
Nice ! 
Couldn't be any easier then that !

HoopsCoop

---

