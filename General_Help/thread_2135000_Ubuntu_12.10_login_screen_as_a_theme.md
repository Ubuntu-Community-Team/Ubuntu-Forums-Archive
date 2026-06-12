---
title: "Ubuntu 12.10 login screen as a theme?"
date: 2013-04-12
forum: General Help
---

### Post by gismo93 on 2013-04-12
Is it possible to change the theme so that my entire system looks like the login screen for ubuntu 12.10? Here's a picture of the login screen. 
(Not mine although mine looks pretty much the same)

[IMG]http://farm9.staticflickr.com/8463/8076773594_e1a8db839d_b.jpg[/IMG]


And here's a picture of my desktop after I've logged in.

[IMG]http://i46.tinypic.com/bkkur.png[/IMG]

I really like the simple, minimalist style to this and would like to apply it system wide. The problem is I can't seem to get any transparency going on in ubuntu at all, even though it's quite obvious my hardware is capable of displaying it. (because the login screen has transparent windows) I've tried changing the transparency in gconf-editor from 1 to 0.5 but there's no difference. I'm not quite sure of my exact hardware specifications but I'm using a Dell Inspiron N5040 laptop.

If somebody could guide me through how to get my desktop to look as close as possible to the login screen I would be very grateful. Thanks in advance!

---

### Post by gismo93 on 2013-04-13
Bump

---

### Post by zombifier25 on 2013-04-13
In 12.10, Unity uses dconf, not gconf. Then again, you should not change g/dconf settings manually yourself.

You can change the top panel to almost transparent, like in the login screen. Install the package compizconfig-settings-manager, open ccsm (note: be very, VERY careful in ccsm), choose the Unity plugin, go to the Experimental tab and decrease the "Panel opacity" settings to just 0.01 (0 would make it disappear completely, leaving only the icons)

As for the GTK+ theme itself, right now there is none.

---

### Post by Zukaro on 2013-04-13
I think "unity-tweak-tool" and "ubuntu tweak" have the ability to do that although I'm not sure.  You can find Ubuntu Tweak in the software center; as for unity tweak tool you'll need to download a ppa or something like that and then download the package (just Google "unity-tweak-tool" and you'll find it).

---

### Post by SantaFe on 2013-04-13
What they said, then if you haven't found the background picture yet, you can just use this as your wallpaper.  It's 1024x768, but it should fill the screen. ;)

Don't ask me how to set it as wallpaper, I use Xubuntu 12.10 and it does it different than Ubuntu, :o

---

### Post by gismo93 on 2013-04-13
Thanks, unity tweak tool did the trick for the top panel and the launcher, but I can't get the window panels to be transparent.

---

### Post by zombifier25 on 2013-04-15
To get a theme similar to the login screen, you'll need a GTK+ theme designed to look like it, which AFAIK there is none, so you can't.

You can make the *entire* window somewhat transparent by getting into ccsm, enable the Opacity, Brightness and Saturation plugin (note: the desktop will freeze for a few seconds), then choose it, go to the "Opacity" tab, click "New", add this into the "Windows" section:
```
!state=maxvert & !state=fullscreen & !state=maxhorz
```
Then modify the Windows values to 85 (or higher or lower, choose one that fits you. If 85 is too transparent/too opaque, choose the setting, click "Modify".

This setting will effectively make all windows and menus transparent EXCEPT for maximized and fullscreen windows - which I'm sure is logical and fits you.

---

