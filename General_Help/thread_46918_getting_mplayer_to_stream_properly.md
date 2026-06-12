---
title: "getting mplayer to stream properly?"
date: 2005-07-06
forum: General Help
---

### Post by gammyhand on 2005-07-06
How do I get mplayer to stream properly? The plugin is working but files I know should buffer after a few seconds don't and it looks like it wants to download the entire file before playing it. I might as well just download the file and have a permanent copy if that is going to always be the case.

---

### Post by Shinitenshi on 2005-07-06
Yah tell me about it, i been looking for that a wile now >.<

---

### Post by gammyhand on 2005-07-06
[QUOTE=Shinitenshi]Yah tell me about it, i been looking for that a wile now >.<[/QUOTE]
 It's a definite annoyance. One of my few with ubuntu.

I have officially dumped windows now (for home use anyway).

---

### Post by Shinitenshi on 2005-07-06
I wanted to also but i have to many problems like the Micromedia issue that i cant solve >.< so i might have to dual boot or somthing

---

### Post by gammyhand on 2005-07-07
[QUOTE=Shinitenshi]I wanted to also but i have to many problems like the Micromedia issue that i cant solve >.< so i might have to dual boot or somthing[/QUOTE]
 Micromedia?

---

### Post by Shinitenshi on 2005-07-07
Yes micromedia dreamweaver final >.<  just doesnt work with me

---

### Post by gammyhand on 2005-07-15
[QUOTE=Shinitenshi]Yes micromedia dreamweaver final >.<  just doesnt work with me[/QUOTE]
 Anyone got an update on streaming?

---

### Post by arunsub on 2005-07-15
My problem is Mplayer plugin for Firefox. If I select high resolution video, it still streams in a small portion on the upper left corner. There's no way I can make the video size big and right click doesn't work. Any suggestion?

---

### Post by arnieboy on 2005-07-15
[QUOTE=arunsub]My problem is Mplayer plugin for Firefox. If I select high resolution video, it still streams in a small portion on the upper left corner. There's no way I can make the video size big and right click doesn't work. Any suggestion?[/QUOTE]
sudo gedit /etc/mplayer/mplayer.conf
set zoom=yes and save and exit. 
U shd see zoom working on streaming videos now.

---

### Post by arnieboy on 2005-07-15
[QUOTE=gammyhand]How do I get mplayer to stream properly? The plugin is working but files I know should buffer after a few seconds don't and it looks like it wants to download the entire file before playing it. I might as well just download the file and have a permanent copy if that is going to always be the case.[/QUOTE]
 upgrade to the latest plugin (mplayerplug-in 2.85). Refer to this thread on how to do it:
[http://ubuntuforums.org/showthread.php?t=44560](http://ubuntuforums.org/showthread.php?t=44560)

---

### Post by arunsub on 2005-07-15
[QUOTE=arnieboy]sudo gedit /etc/mplayer/mplayer.conf
set zoom=yes and save and exit. 
U shd see zoom working on streaming videos now.[/QUOTE]
Thanks. I'll try that.

---

### Post by gammyhand on 2005-07-16
[QUOTE=arnieboy]upgrade to the latest plugin (mplayerplug-in 2.85). Refer to this thread on how to do it:
[http://ubuntuforums.org/showthread.php?t=44560](http://ubuntuforums.org/showthread.php?t=44560)[/QUOTE]
Thanks :)

---

