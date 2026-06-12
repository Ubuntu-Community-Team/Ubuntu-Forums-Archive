---
title: "KTorrent won't load after sleep, etc"
date: 2012-10-18
forum: General Help
---

### Post by Stonecold1995 on 2012-10-18
Sometimes when I put my computer in sleep mode, or log out, or kill Xorg, etc, KTorrent won't start up next time until I reboot.  The window will open, but it stays blank and unresponsive (it won't even respond to SIGTERM, so I have to use SIGKILL), and the icon that should be in the task bar is blank (or transparent)..  I tried deleting the lockfile (/tmp/.ktorrent_kde4_1000.lock) but that didn't work.  Even using "kill -9 -1" doesn't work, so I'm assuming there's a stale file left over somewhere that's preventing KTorrent from opening.  I tried looking in /tmp, but couldn't find anything (I used "grep -ir ktor /tmp").  This is what KTorrent looks like when I try opening it at times like these:
[[img]http://www.pictureshack.us/thumbs/33855_screenshot.png[/img]](http://www.pictureshack.us/images/33855_screenshot.png)

Does anyone have any ideas how I can get KTorrent to run without rebooting when this happens?

**EDIT: After upgrading to Kubuntu 12.10 this doesn't seem to be happening anymore, but I'll see if it happens again.**

---

