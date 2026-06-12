---
title: "&quot;Pin to Favorites&quot; option missing"
date: 2019-04-30
forum: General Help
---

### Post by ytterbious on 2019-04-30
I want to pin a program to my dock but the right-click option is missing whenever it's running. I also want to add an icon to it. I was thinking I could make a launcher/.desktop file but it doesn't seem to work, but maybe I've messed something up. 

Can anybody clarify what I could do? Thanks mates :KS:p.

---

### Post by olivers123 on 2019-04-30
> **ytterbious said:**
> I want to pin a program to my dock but the right-click option is missing [[COLOR=#000000]gimp[/COLOR]]("https://gimp.software/") [[COLOR=#000000]freejobalert[/COLOR]]("https://freejobalert.vip/") [[COLOR=#000000]notepad++[/COLOR]]("https://notepad.software/") whenever it's running. I also want to add an icon to it. I was thinking I could make a launcher/.desktop file but it doesn't seem to work, but maybe I've messed something up. 

Can anybody clarify what I could do? Thanks mates :KS:p.
It doesnt work for me either but i thought that it was meant to be like that. Is this a bug/glitch?

Help is appreciated.
Thanks in advance,
Regards,
Oliver

---

### Post by #&amp;thj^% on 2019-04-30
Try this for me please.
Open Terminal and run:
```

gsettings get org.gnome.shell favorite-apps
```

You should get the list of .desktop files associated to the apps pinned to Ubuntu dock in order, something like the following:

['appname-1.desktop', 'appname-2.desktop', 'appname-3.desktop', 'appname-4.desktop', 'appname-5.desktop']
Mine shows like:
```
gsettings get org.gnome.shell favorite-apps
['firefox.desktop', 'org.gnome.Nautilus.desktop', 'yelp.desktop', 'org.gnome.Terminal.desktop', 'firetools.desktop', 'org.gnome.tweaks.desktop', 'conky-manager.desktop']

```

Suppose you want to pin the app caja.desktop file as the second item in the dock. In that case, run
```

gsettings set org.gnome.shell favorite-apps "['appname-1.desktop', 'caja.desktop', 'appname-2.desktop', 'appname-3.desktop', 'appname-4.desktop', 'appname-5.desktop']"

```

---

