---
title: "Dropbox widget?"
date: 2015-02-07
forum: General Help
---

### Post by cesaro.angelo on 2015-02-07
Hi,
 are there some widgets to use dropbox in gnome3?
thanks

---

### Post by v3.xx on 2015-02-07
Widgets suggest that you want a active display of some sort.  Are you syncing to dropbox and want to monitor it?

---

### Post by cesaro.angelo on 2015-02-07
yes if it's possible I'd like to have a sync and monitor function mainly.

---

### Post by buzzingrobot on 2015-02-07
I'm not aware any of but check extensions.gnome.org.

The actual Dropbox binary is proprietary. Right-clicking on the Dropbox icon should display a menu of behaviors that proprietary offers.

Annoyingly, after a recent update by Dropbox, many users of different desktop environments have noticed the icon either does not appear, seems to appear randomly, or is, in  effect, invisible (if you can find the space it is occupying, a right click may work as usual.)

---

### Post by cesaro.angelo on 2015-02-07
no using gnome3 I never noticed any icons on the bar on the top of my desktop. I have installed dropbox downloading it directly from dropbox site.

---

### Post by sandyd on 2015-02-07
> **cesaro.angelo said:**
> no using gnome3 I never noticed any icons on the bar on the top of my desktop. I have installed dropbox downloading it directly from dropbox site.

Bugs (Dropbox now has QT Interface)
[https://bugreports.qt.io/browse/QTBUG-31762](https://bugreports.qt.io/browse/QTBUG-31762)
[https://bugreports.qt.io/browse/QTBUG-43859](https://bugreports.qt.io/browse/QTBUG-43859)

Known problem in....
XFCE (Thread includes fix): [https://www.dropboxforum.com/hc/communities/public/questions/201545695-After-upgrade-to-3-x-the-dropbox-tray-icon-is-missing-XFCE-Xubuntu-14-04-1-x64-?page=2](https://www.dropboxforum.com/hc/communities/public/questions/201545695-After-upgrade-to-3-x-the-dropbox-tray-icon-is-missing-XFCE-Xubuntu-14-04-1-x64-?page=2)
Gnome: [https://www.dropboxforum.com/hc/communities/public/questions/201896285-Top-bar-tray-icon-missing-Fedora-21](https://www.dropboxforum.com/hc/communities/public/questions/201896285-Top-bar-tray-icon-missing-Fedora-21)
Cinnamon: (No idea if this dropbox bug exists due to cinnamon bug in link) [https://github.com/linuxmint/Cinnamon/issues/2846](https://github.com/linuxmint/Cinnamon/issues/2846)

---

### Post by v3.xx on 2015-02-07
Depending on how much eye candy you can handle, conky seems to do this.  I do not use it myself.
[https://www.google.com/search?q=conky+dropbox&ie=utf-8&oe=utf-8](https://www.google.com/search?q=conky+dropbox&ie=utf-8&oe=utf-8)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=conky&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=conky&sa=Search&cof=FORID:9)

---

### Post by PhilGil on 2015-02-07
> **v3.xx said:**
> Depending on how much eye candy you can handle, conky seems to do this.  I do not use it myself.
[https://www.google.com/search?q=conky+dropbox&ie=utf-8&oe=utf-8](https://www.google.com/search?q=conky+dropbox&ie=utf-8&oe=utf-8)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=conky&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=conky&sa=Search&cof=FORID:9)

The dropbox icon has been hit-and-miss for me on Gnome since the update. When it fails I've been using conky.

Here's my .conkyrc. It's very basic; just displays the Dropbox status in the upper left corner of my screen.

```

alignment top_left
use_spacer none
gap_x 10
gap_y 30
own_window_argb_visual yes
own_window_transparent yes
border_width 1
cpu_avg_samples 2
default_color white
use_xft yes
xftfont Sans Bold:size=10.5
# no_buffers yes
own_window yes
own_window_class Conky
own_window_type desktop
update_interval 1.0
text_buffer_size 500
minimum_size 500 200
double_buffer yes

TEXT
Dropbox Status: ${execi 6 dropbox status}

```

---

