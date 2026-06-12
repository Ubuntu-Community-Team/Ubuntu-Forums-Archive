---
title: "tip on getting newest Adobe flash player to work"
date: 2007-11-12
forum: General Help
---

### Post by os.getlogin on 2007-11-12
I recently upgraded from to Gutsy (7.10) from Feisty (7.04) and found some problems with certain sites that require the newest flashplayer.  For example, the 24-hour stream at [http://www.npr.org]("http://www.npr.org") or the main winodw at [http://www.earthcam.com/]("http://www.earthcam.com/").

The solution is easy, but took me a while.  First, I made sure that I had the Adobe (non-free) plugin installed:
```

% sudo apt-get --purge remove flashplugin-nonfree
% sudo apt-get install  flashplugin-nonfree

```

Then checked in Firefox (enter in the url):
```

about:plugins

```
Flash 9.0x should be installed.  Now for me, it also listed Flash 7x, so I removed the flash items in ~/.mozilla/plugins:
```

% cd ~/.mozilla/plugins
% rm *flash*

```
  and it works.

Again, a simple solution, but perhaps it will help someone.

Cheers!

---

