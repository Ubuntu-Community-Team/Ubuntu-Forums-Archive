---
title: "[SOLVED] Cross-Platform Bittorent Client"
date: 2007-08-08
forum: General Help
---

### Post by guguma on 2007-08-08
I am running Ubuntu Feisty 7.04 but I also run XP. The problem is I do my torrent downloads from one of them only so when I switch the OS I hamper my downloads. I thought maybe a Cross Platform bittoret client can continue the unfinished torrents form either of the OS's. 

Is there something like that. Or are there other solutions to this.

By the way I am using utorrent as a bittorent client but I may switch.

Thanks in advance

---

### Post by PentaxFollower on 2007-08-08
UTorrent works fine under Wine. You don't have to even install it, just copy and run executable. I use it that way, it continues downloading if all paths are set just like in Windows installation. There is only one problem with minimizing/maximizing uTorrent's window (maybe it's already solved in newest version or maybe it's only my system's issue). Anyway - it can be avoided by clicking on uT's tray-icon to make window fullscreen again.

(sorry for my poor english:) )

---

### Post by OoooMatron on 2007-08-08
azureus is cross platform.

---

### Post by guguma on 2007-08-08
All right then I can use utorrent but there are several more questions regarding this issue. The paths I normally use are on my ntfs partitions and I think that it will cause problems. Also I have no idea what Wine is. Can someone explain it to me.

---

### Post by PentaxFollower on 2007-08-08
NTFS partitions are no problem if you'll use NTFS-3G driver to mount them:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=switch+ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=switch+ntfs-3g")
Switching to NTFS-3G is almost painless, just follow the tutorial. This driver is good thing to have.

Wine is "compability layer" that allows you to use a lots of windows aplications. I'm sure you'll find many HOWTOs and forum threads about installing and using it. If you'll find it too dificult (i doubt it :) ), you can also install Wine from Automatix (use 'search' for more info).

Azureus is another option. It's writen in Java so it's naturaly multiplatform app, but i don't know if it can import your current downloads.

edit: it's possible that you already have ntfs-3g. Look into /etc/fstab file to see if there are filesystem(s) of ntfs-3g type.

---

### Post by guguma on 2007-08-08
Thanks for all your help I have done wine + utorrent + ntfs-3g and everything works fine. And I guess that wine is just an acronym for Wine is not an Emulator right? Everything is an acronym in LINUX. :)

---

### Post by OoooMatron on 2007-08-09
> **guguma said:**
> Thanks for all your help I have done wine + utorrent + ntfs-3g and everything works fine. And I guess that wine is just an acronym for Wine is not an Emulator right? Everything is an acronym in LINUX. :)

oh yeah, i'm sure that was intelligent guess ;)

:lolflag:

---

