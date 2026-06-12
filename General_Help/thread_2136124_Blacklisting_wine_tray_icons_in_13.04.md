---
title: "Blacklisting wine tray icons in 13.04?"
date: 2013-04-16
forum: General Help
---

### Post by bilalqayum on 2013-04-16
There has been a lot of stuff written about the shift in tray icons and indicators in 13.04 but almost all are diametrically opposed to what I usually do whenever installing a new version of Ubuntu. I use a handful of wine (or in my case CrossOver Linx) apps on a regular basis, and one of them in particular, Evernote, has a hideous tray icon that nests itself in the panel.

I can no longer blacklist Wine/CrossOver apps from showing up in the panel like normal, is there possibly another way to achieve the desired outcome? I know there are a handful of Evernote native clients but none have worked particularly well for me, and I've been quite happy so far with my CrossOver investment. 

Any help in blacklisting these icons from the panel would be much, much appreciated.

---

### Post by kostkon on 2013-04-16
Have you tried replacing the evernote tray icon with a better one, it might be possible somehow, maybe find and replace the icon file, if it isn't embedded in the executable.

Also, did you check for any revelant options in the settings?

---

### Post by bilalqayum on 2013-04-16
I'd be happy to try and replace the icons, that hadn't occurred to me actually. Although I'm not actually finding any relevant icon files so I suspect this may be embedded.

There are no options in the settings to turn off the tray-icon unfortunately.

---

### Post by mc4man on 2013-04-16
You could use this ppa which returns the whitelist to 13.04 ppa
[https://launchpad.net/~timekiller/+archive/unity-systrayfix](https://launchpad.net/~timekiller/+archive/unity-systrayfix)

or build unity & remove wine from the included non user configurable  whitelist
(currently unity-7.0.0daily13.04.15/panel/PanelTray.cpp line 33, the number of listed has to match the blue
const std::array<std::string, [COLOR="#0000CD"]2[/COLOR]> WHITELIST {{ "JavaEmbeddedFrame", "Wine" }};

ppa is likely more convenient if it stays updated thru release

---

### Post by bilalqayum on 2013-04-16
Ah, that ppa sounds like just the solution. Many thanks.

---

