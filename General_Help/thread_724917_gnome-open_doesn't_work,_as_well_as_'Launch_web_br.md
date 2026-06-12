---
title: "gnome-open doesn't work, as well as 'Launch web browser' shortcut"
date: 2008-03-15
forum: General Help
---

### Post by Joe_Bishop on 2008-03-15
OOPS, It is about Hardy Heron.

I didn't post it in the launchpad, because I don't know which package the gnome-open comes with, and apt-cache search gnome-open didn't show anything.
Well, the bug report tool use gnome-open for launching web browser, but it doesn't work:
```
master@master:~$ gnome-open http://forum.local
Error showing url: There was an error launching the default action command associated with this location.

```
When I use keyboard shortcut for web browser, I get the windows with error message (see the shot in attachment).
I put firefox-3.0bXpre nightly builds later, but now I use current firefox-3.0b4 from repo (Hardy Heron)

---

### Post by Joe_Bishop on 2008-03-15
Everything now works. I just checked if the firefox is the default browser.

---

### Post by RandyNose on 2008-05-11
Joe, I had the same problem, but I had to change the default browser to reflect the change of Firefox, to Firefox-2 %s in the preferred applications. 
I did want Firefox 3, as it doesn't support some of my favorite Add Ons. I'd  have been happy if it had added FireFox 3 as an Alt Browser rather then replacing the old one.

---

### Post by Joe_Bishop on 2008-05-12
You should check this in the Firefox-2 settings (Edit->Preferences->General)
[IMG]http://img-fotki.yandex.ru/get/21/denis-cheremisov.5/0_1035f_e0c2981b_orig[/IMG]

---

