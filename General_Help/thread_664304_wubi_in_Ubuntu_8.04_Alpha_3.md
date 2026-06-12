---
title: "wubi in Ubuntu 8.04 Alpha 3?"
date: 2008-01-11
forum: General Help
---

### Post by siddharth.unnikrishnan on 2008-01-11
hey...

just wanted to know whether Wubi is included along with Ubuntu 8.04 Alpha 3....or have new versions of Wubi been made for 8.04?

regards,
Siddharth.

---

### Post by ago on 2008-01-11
I have it working at home ;)


Alpha3 still includes the old cdboot version. There are a few patches I have submitted to other ubuntu devs that should be merged upstream today/tomorrow, so early 8.04 builds may come this w/e or the coming week. From Ubuntu alpha 4 the full wubi version should be included.

---

### Post by mikedep333 on 2008-01-11
> **ago said:**
>  From Ubuntu alpha 4 the full wubi version should be included.

Awesome. Keep up the great work.

---

### Post by siddharth.unnikrishnan on 2008-01-11
hey....

thanks for da reply ago... as i said before, im runnin outta patience now! :)

keep up the great work...
all da best...

:)

---

### Post by siddharth.unnikrishnan on 2008-01-29
hey....

i tried installing  Wubi-8.04-developerpreview-rev392 and v393 using alpha 1 and alpha 3 both which i had previously downloaded. heres the thing.... rev393 doesnt boot up ubuntu atall...i get the ubuntu logo with the bar and it stays like that forever... but rev392 does only when i use alpha 1... it went smoothly till it came to loading bluetooth services and after that stays like that without any activity...i restarted my laptop and chose for the safe graphics mode and viola...it passed bluetooth services and then loaded ubiquity...

the first screen i get when ubiquity loads is the time zone selection window after which i clickd on the forward button... then it tries to load the partitioner and it fails... when i wait for a few seconds i get an error and a confirmation whether to 'continue anyway' or 'try again'... when i click on 'try again' i see my HDD light blinking periodically in equal intervals but nothing ever happened even after i waited for more than 40 minutes... then when i clicked cancel...it took me to the ubuntu live session user mode... just the way it looks when you boot from a live cd... so i restarted the laptop, chose the safe graphics mode, it went again to ubiquity, partitioner fails and when i get the confirmation, this time i click on 'continue anyway'. but this time i see no blinking hdd lights. the system stays just like that with the time zone selection window after which, when i click on 'cancel'.. i get back to the live session mode....

i have an HP dv6500t, 1.6ghz 667mhz fsb, 2gb, 120gb and geforce 8400....

hope i helped in some way... :)

also...please advice!

regards,
Siddharth.

---

### Post by ago on 2008-01-30
> **siddharth.unnikrishnan said:**
> 
the first screen i get when ubiquity loads is the time zone selection window after which i clickd on the forward button...
Nope that's not correct you should only see progress bars, ubiquity should run in unattended mode. Note that it is important to use the latest daily build hardy-desktop ISO, old ISOs will NOT work. In fact as of yesterday there are still 2 patches missing in the ISO that have to be merged, 1 affects menu.lst (booting), 1 affects umountfs (rebooting).

---

### Post by ago on 2008-01-30
All urgent patches should be in now, hardy-desktop ISO builds released tonight+ might even work...

---

