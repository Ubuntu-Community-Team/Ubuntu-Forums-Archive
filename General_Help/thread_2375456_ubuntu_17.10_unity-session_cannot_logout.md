---
title: "ubuntu 17.10 unity-session cannot logout"
date: 2017-10-24
forum: General Help
---

### Post by monkeybrain20122 on 2017-10-24
As the title says, "logout" doesn't work for unity-session in Artful, it just freezes and a hard power off is needed (it seems that logout doesn't work in gnome-wayland eithe, but haven't tried much)

---

### Post by mc4man on 2017-10-24
Did you just add unity-session or did you add it & lightdm  & remove ubuntu-session, gdm3, gnome-shell & whatever else isn't needed in a unity session?

---

### Post by monkeybrain20122 on 2017-10-24
> **mc4man said:**
> Did you just add unity-session or did you add it & lightdm  & remove ubuntu-session, gdm3, gnome-shell & whatever else isn't needed in a unity session?

It coexists with gnome. Tried both gdm and lightdm, can't logout with either.

---

### Post by mc4man on 2017-10-24
I've found it's better just one or the other.
Was this working then all of a sudden not?

Here I basically installed unity-session & lightdm & removed

> Completely removed the following packages:
gdm3
gir1.2-gdm-1.0
libgdm1
ubuntu-desktop
gnome-shell
gnome-shell-extension-appindicator
gnome-shell-extension-ubuntu-dock
ubuntu-session
gnome-shell-common
gnome-themes-standard-data
gnome-screensaver
gnome-themes-standard
caribou
gir1.2-caribou-1.0
libcaribou-common
libcaribou0
adwaita-icon-theme-full


---

### Post by monkeybrain20122 on 2017-10-24
Thanks for the reply.

It seems that this is due to some residual configurations in 17.04 since I kept the same /home partition even though I reinstalled the OS. I had the same problem with 17.04 (couldn't logout) I tried a completely fresh install on an external drive then booted off the same machine the problem disappeared, it logged out with no problem (with gdm)

---

