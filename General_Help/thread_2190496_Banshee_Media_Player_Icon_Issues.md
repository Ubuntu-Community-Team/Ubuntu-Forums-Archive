---
title: "Banshee Media Player Icon Issues"
date: 2013-11-27
forum: General Help
---

### Post by swhit3 on 2013-11-27
I'm using Ubuntu 13.10, running the latest Banshee 2.6.1 and for some reason when I alt-tab the Banshee icon is very small and very pixelated. Any thoughts on to why this is, if I can fix it or if it's a bug? I've been having a lot of issues with 13.10 in general, kinda miss 13.04, but the geek in my always likes to stay as up to date as possible. Also when I use the dash, the Banshee icon is much smaller than all the other icons. Any thoughts? Any help is appreciated! See screenshots for clarification.


[ATTACH=CONFIG]248141[/ATTACH][ATTACH=CONFIG]248140[/ATTACH]

---

### Post by mc4man on 2013-11-27
By default banshee.desktop should be using Icon=media-player-banshee which looks fine here both in the Dash & alt-tab switcher. (icon is located in /usr/share/app-install/icons

You could check /usr/share/applications/banshee.desktop & see

Do you have another banshee.desktop somewhere like /usr/local/share/applications or ~/.share/applications?

It looks like you're using Icon=banshee which would use /usr/share/pixmaps/banshee.xpm

---

### Post by swhit3 on 2013-11-28
I purged and reinstalled Banshee and the icons went back to normal! However, as soon as I restarted my laptop, the icons went back to being tiny and pixelated, I don't understand why, any suggestions?

---

