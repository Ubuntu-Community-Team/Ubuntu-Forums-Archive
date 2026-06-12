---
title: "Won't even boot up? Goes to BusyBox"
date: 2008-06-16
forum: General Help
---

### Post by ajwak95 on 2008-06-16
Dang this BusyBox. Okay, well heres how I installed ubuntu. I used Wubi, why else would I be here. When i boot i dont go to the menu, i try to boot into ubuntu. Well I can't even log on, I get the BusyBox. Then I reboot and try to go into safe mode, I do that and was able to get in to ubuntu a couple of times, but now I get to the part of where my DVD drive needs an update and then It just stops? I am totally lost and I kind of want to go to 7.10 ubuntu but there is no Wubi for it. If there is please give me a link and I will use that, for internet also. and I have another problem, when I try to connect to wireless internet, it crashes the modem its on! please help with the wubi and the internet!

---

### Post by ajwak95 on 2008-06-16
Bump, sorry but I really need to get this figured out.

---

### Post by ajwak95 on 2008-06-17
WOW. All these views and not one answer. humph.

---

### Post by ago on 2008-06-17
Not clear when this happens, is it at first installation, or after installation you got a usable system that then became unbootable? was this after some upgrades?

Run chkdsk /r from windows on the same drive where you installed wubi and in the second case try to press esc at boot and select an old kernel and/or recovery mode

---

### Post by ajwak95 on 2008-06-17
> **ago said:**
> Not clear when this happens, is it at first installation, or after installation you got a usable system that then became unbootable? was this after some upgrades?

Run chkdsk /r from windows on the same drive where you installed wubi and in the second case try to press esc at boot and select an old kernel and/or recovery mode

ok. Well I install it on ubuntu. Then i reboot, then I somehow get the BusyBox. Now this hasn;t been a problem on this one. Let me get on right now and check. Kernal alive message and the loading screen and then the busy box thing shows up. No upgrades.

---

### Post by ajwak95 on 2008-06-17
okay heres what I got on the safeboot one of the Alerts was "/host/ubuntu/disks/root.disk does not exist. Dropping to a shell!" and every stinking time i do it on the install, it does that.

---

### Post by ago on 2008-06-17
> **ajwak95 said:**
> okay heres what I got on the safeboot one of the Alerts was "/host/ubuntu/disks/root.disk does not exist. Dropping to a shell!" and every stinking time i do it on the install, it does that.

well check if it you can see C:\ubuntu\disks\root.disk from windows (change the drive letter as appropriate). If it is not there either it was deleted by mistake or the filesystem got corrupted because of hard reboot (look for hidden files called found000 in c:\ or c:\ubuntu)

---

