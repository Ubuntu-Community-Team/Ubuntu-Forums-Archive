---
title: "how do I set icon theme for specific applications"
date: 2017-12-17
forum: General Help
---

### Post by ardouronerous on 2017-12-17
I have a few applications that aren't playing nice with my favorite GTK theme and icon theme.

I was able to learn how to set a different GTK theme for specific applications: [https://ubuntuforums.org/showthread.php?t=1340828](https://ubuntuforums.org/showthread.php?t=1340828)

Now, I'd like to know if setting a different icon theme for specific applications is possible.

Thanks.

---

### Post by vasa1 on 2017-12-17
The thread you linked to deals with gtk2 applications. For gtk3 applications try something like:```
GTK_THEME=Adwaita:dark gnome-calculator
```from [https://wiki.archlinux.org/index.php/GTK%2B](https://wiki.archlinux.org/index.php/GTK%2B)

I haven't come across a way to make only some applications use one icon theme and the rest to use another. It *may* be possible with gtk3 apps if you have different settings.ini files in each gtk3 folder of your themes.
```
[Settings] 
gtk-icon-theme-name=gnome
```
I haven't looked into this myself!

---

### Post by ardouronerous on 2017-12-17
Thanks for the reply.

How do I determine if my app is a gtk3 application?

---

### Post by vasa1 on 2017-12-17
Example:```
$ apt show gedit | grep libgtk-3-0

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Depends: python3:any (>= 3.3.2-2~), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libenchant1c2a (>= 1.6.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libgirepository-1.0-1 (>= 0.9.3), libglib2.0-0 (>= 2.44), **libgtk-3-0** (>= 3.16.2), libgtksourceview-3.0-1 (>= 3.18.0), libpango-1.0-0 (>= 1.14.0), libpeas-1.0-0 (>= 1.1.0), libx11-6, libxml2 (>= 2.7.4), gir1.2-gtk-3.0, gir1.2-gtksource-3.0, gedit-common (>= 3.18), gedit-common (<< 3.19), gsettings-desktop-schemas, python3-gi (>= 3.0), python3-gi-cairo (>= 3.0), gir1.2-peas-1.0, gir1.2-glib-2.0, gir1.2-pango-1.0, libpeas-1.0-0-python3loader, iso-codes
$ 
```

---

