---
title: "Disable Desktop Icons - Trash Can"
date: 2016-10-04
forum: General Help
---

### Post by sed_faster on 2016-10-04
Hello everyone,

I am creating a script for my installation in Lubuntu 16.04 LTS. And I am trying disable the icon trash in desktop. I can did this through  button right, on desktop, Desktop Preferences, label "Desktop Icons" and disable option "Show "Trash Can" folder on the desktop".
But I want do this through terminal. How can do I this?

I trying this, but I can't have success:
```

conf_desktop="
[*]
wallpaper_mode=center
wallpaper_common=1
wallpapers_configured=1
wallpaper0=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
wallpaper=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
desktop_bg=#2e4060
desktop_fg=#ffffff
desktop_shadow=#000000
desktop_font=Ubuntu 11
show_wm_menu=0
sort=mtime;ascending;
show_documents=0
show_trash=0
show_mounts=1"
sudo echo $conf_desktop > ~/.config/pcmanfm/lubuntu/desktop-items-0.conf
sudo echo $conf_desktop > ~/.config/pcmanfm/lubuntu/desktop-items-1.conf
sudo echo $conf_desktop > ~/.config/pcmanfm/lubuntu/desktop-items-2.conf

```
The parameter "show_trash" remains unchanged after reboot!

Thanks

---

