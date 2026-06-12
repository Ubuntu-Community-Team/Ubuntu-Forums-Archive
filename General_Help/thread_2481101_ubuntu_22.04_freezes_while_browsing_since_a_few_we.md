---
title: "ubuntu 22.04 freezes while browsing since a few weeks"
date: 2022-11-19
forum: General Help
---

### Post by wesselaar2 on 2022-11-19
[COLOR=#333333][FONT=Verdana][COLOR=#000000][FONT=&amp]Having a problem for a few weeks now with debian 11 gnome and ubuntu 22.04 gnome on 2 dell optiplex 7020 computers  . 
for example: browsing youtube or twitter results in a total freeze within minutes. no other problems with video or music software or filemanager or gnome-terminal.
Thought it would be a ssd problem but switching the ssd into the other pc (same model pc dell optiplex 7020) gives the same issue. switch off hardware acceleration in chrome doesnt solve the issue neither does the use of firefox solves it. 
a long test with memtest says the memory is also ok on both computers. 
tried different (also a new one) ssd disks. also bought few new sata cables, didnt help. 
i thought it would be a ssd issue but isnt, a new 500gb ssd samsung also freezes... 
also tried to use the vga video output instead of display-port, didnt help.

even after many updates (even regular kernel update) problem is still there. 
i cant find anything that looks similar on the web acording to this issue. Windows 10 seems to work flawless but got used to debian/ubuntu since 2010 so i hope there is a solution for this.
Does this sounds as a known problem to anyone? [/FONT][/COLOR]



[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][Top]("https://forums.debian.net/viewtopic.php?p=762911#top")[/FONT][/COLOR]

---

### Post by wesselaar2 on 2022-11-19
> **freedomreignsterror said:**
> I am using Xubuntu 22.04.1 and I am experiencing the same thing. One correlation is with the Appearance themes. When I use Greybird-dark, it freezes more regularly. When I use the Adwaita-dark theme it doesn't freeze until much longer. So, this leads me to thinking it has to do with possibly the RAM. I have 4 GB which I would think is more than enough, but perhaps with multiple browsers and using a USB dongle it needs more RAM?


I have 8 gb and gnome with standard theme (minimal installation) memory consumption is far from 8gb (system monitor) when it freezes. mostly around 2 or 3 gb with gnome.  Xubuntu uses less ram.

---

### Post by vmpx on 2022-11-27
I use in GRUB "nomodeset quiet splash" (Ubuntu 18.04 and 20.04)

---

### Post by wesselaar2 on 2022-12-02
[COLOR=#000000]"nomodeset quiet splash" doenst do the trick here.  it keeps freezing while browsing in chrome of firefox. i installed windows 10 on the ssd where ubuntu was at and having no problems.
Installed ubuntu on a new ssd and problem is there again. so it looks to me that its a softwareproblem.  im hoping an upcoming update will solve it. till then ill use windows for a while[/COLOR]

---

