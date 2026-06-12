---
title: "retro desktop theme of winxp"
date: 2008-05-01
forum: General Help
---

### Post by h4mx0r on 2008-05-01
I used xubuntu and threw together some old windows xp themes because some people just get stuck to their old "halloween eyecandy" as they say ;) No clue how far you will get on ubuntu or kubuntu. Still looking for a nice BSOD usplash to lol at.

-gdm login manager-
[http://www.gnome-look.org/content/show.php/Windoze+Professional?content=53906](http://www.gnome-look.org/content/show.php/Windoze+Professional?content=53906)

-splash screen-
[http://www.gnome-look.org/content/show.php/Windows+XP+Login?content=57773](http://www.gnome-look.org/content/show.php/Windows+XP+Login?content=57773)

-mouse icon- (closest I could find)
[http://www.gnome-look.org/content/show.php/Cursor+XP?content=77833](http://www.gnome-look.org/content/show.php/Cursor+XP?content=77833)

-window manager-
redmondxp

-user interface-
xfce-redmondxp

-icons-
[http://www.gnome-look.org/content/show.php/GnomeXP?content=69587](http://www.gnome-look.org/content/show.php/GnomeXP?content=69587)

-background- (do not use that program it will jack your system up, just the background)
[http://www.xpde.com/releases/xpde-0.5.1.tar.gz](http://www.xpde.com/releases/xpde-0.5.1.tar.gz)

-applications button-
[IMG]http://i26.tinypic.com/2eaidzm.png[/IMG]

-icons and panel- (make the file named .gtkrc-2.0 in your /home)
[B]
~/.gtkrc-2.0[/B]
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0
    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#00ff00"
    fg[ACTIVE] = "#0000ff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

style "panel"
{
bg[NORMAL] = "#255fdc"
xthickness = 0
ythickness = 0
}
widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"


_**OPTIONAL**_
-bill gates blowing up your computer-
[http://xpenguins.seul.org/](http://xpenguins.seul.org/)

-amsn skin-
[http://www.amsn-project.net/getURL.php?id=29](http://www.amsn-project.net/getURL.php?id=29)

-ies4linux because no other program would dare use that theme-
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by macaholic on 2008-05-01
I never quite understood these windows XP themes, I guess for disguising ubuntu so people don't know, but I can't imagine actualy thinking that the XP theme looks GOOD. Just my opinion.

---

### Post by h4mx0r on 2008-05-13
Yeah it doesn't look good really. But the style of its default background with the field is more well played out in the other background I supplied. And the gnomexp icons list what sort of media is in optical drives be it dvd or cd-rw and etc. Some people dislike those backdrops shadows on icons and have no clue how to remove it so its nice to mention how.

I have yet to find a way to highlight the text of icons so that with a white background it would still be readable yet without a backdrop icon shadow thing.

---

