---
title: "themes deleted"
date: 2008-05-28
forum: General Help
---

### Post by sithpigeon on 2008-05-28
I was trying to install some extra themes for gnome and all my themes got deleted. I don't know how but I would like to re-install the basic group of themes that came with ubuntu. If anyone knows how to do this from the cd or knows of a download that would be great cause I'm stuck using the crappy raleigh theme. thanks

---

### Post by Forlong on 2008-05-28
Install ubuntu-desktop:
```
sudo apt-get install ubuntu-desktop
```
That is a meta-package which should install all the default packages you may have deleted.

---

### Post by sithpigeon on 2008-05-28
sorry about the long wait

I tried that but it says its already fully installed. I just need to re-add the theme files.

---

### Post by Forlong on 2008-05-29
```
sudo apt-get install gnome-themes gnome-accessibility-themes human-theme
```
Those include are all the default themes AFAIK

---

