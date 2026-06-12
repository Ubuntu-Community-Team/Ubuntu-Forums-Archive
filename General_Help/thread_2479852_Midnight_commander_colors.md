---
title: "Midnight commander colors"
date: 2022-10-10
forum: General Help
---

### Post by spongecake2 on 2022-10-10
Hello all,

I'm trying to get the same colours/theme for midnight commander (mc) across my servers (less harsh on my eyes)

When I install Ubuntu in VirtualBox I get this theme with the colours I want :-

[IMG]https://i.postimg.cc/1Xc64JxD/mc-virtual.png[/IMG]

If I ssh in,  I get the standard blue colour :-

[IMG]https://i.postimg.cc/W3V0VQCs/mc-vm.png[/IMG]


I'm guessing it's some kind of colour translation going on  - where would I need to look to see what's happening. 

Thanks

Spongecake2

---

### Post by Holger_Gehrke on 2022-10-10
The first thing I'd check is the environment variable TERM. After that I'd check the settings in ~/.config/mc/ini. If I wanted a theme of my own, the available themes are in /usr/share/mc/skins/ and skins of your own can go in ~/.local/share/mc/skins/.
For more details check the manual page for mc.

Holger

---

