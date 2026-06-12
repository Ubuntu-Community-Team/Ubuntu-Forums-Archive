---
title: "Lock screen is not working"
date: 2021-03-01
forum: General Help
---

### Post by praneetarora on 2021-03-01
I am unable to lock my screen. Even after suspending my system, lock screen feature doesn't seem to work. The super key + L combo is also not working. I thought the problem was caused by some gnome extensions, so I tried to remove them. But, I accidentally removed system wide extensions using this command - sudo rm -r /usr/share/gnome-shell/extensions/

And now I am unable to see my ubuntu-dock and certain apps which use to appear on top right corner are also not appearing( ubuntu-appindicators).

Someone kindly help.

---

### Post by HermanAB on 2021-03-01
My solution would be to install the XFCE desktop and forget about Gnome, since fixing Gnome will likely be very hard.
[https://technastic.com/install-xfce-desktop-environment-on-ubuntu/](https://technastic.com/install-xfce-desktop-environment-on-ubuntu/)

---

### Post by deadflowr on 2021-03-01
```
sudo apt install --reinstall ubuntu-desktop
```
that should fix/restore the missing extensions.

As far as lock screen goes, look in Settings >> Privacy at the Screen lock settings.

---

