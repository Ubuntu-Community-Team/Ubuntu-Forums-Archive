---
title: "Image snipping tool for screen capture instead of printscreen"
date: 2018-10-20
forum: General Help
---

### Post by iamtheeggman2 on 2018-10-20
Hi,

In windows there is an image snipping tool which lets you select an area of the screen and save that as an image instead of you having to do a print screen of the entire screen and then have to paste into an image program for saving, is there one like this for lubuntu?

Thanks in advance!

---

### Post by coffeecat on 2018-10-20
With the Unity and Mate desktops, simply pressing shift + printscreen gives you a snipping tool. I have no idea whether Lubuntu does the same. Give it a try.

---

### Post by iamtheeggman2 on 2018-10-20
Thanks, is there a name for the feature? Can you see it in task manager when you use it? Are there any advantages to unit and mate desktops?

---

### Post by &amp;KyT$0P# on 2018-10-20
It's not a feature of the desktop environment.  It's a program.

If I'm remembering right, the default in Lubuntu is [FONT=Courier New]scrot[/FONT] which you can also run from a Terminal -
```
scrot -s
```
If you prefer something with a GUI, there are other "snipping tool" type screenshot programs available in the Ubuntu repositories, e.g. gnome-screenshot.

---

### Post by iamtheeggman2 on 2018-10-20
the command allowed me to saw of drag a square over a piece of screen, then i went to abi word and tried to paste as an image but nothing happened?

also, how do i put this into an icon for easier use on the desktop?

---

### Post by &amp;KyT$0P# on 2018-10-20
> **iamtheeggman2 said:**
> the command allowed me to saw of drag a square over a piece of screen, then i went to abi word and tried to paste as an image but nothing happened?
The screenshot went to a file, that is located in whatever your Terminal's working directory was when you ran the command.

> also, how do i put this into an icon for easier use on the desktop?
You need to create a .desktop file, see [this thread]("https://ubuntuforums.org/showthread.php?t=2394848&p=13778034&viewfull=1#post13778034") for what to put in it.

---

### Post by iamtheeggman2 on 2018-10-20
> **halogen2 said:**
> It's not a feature of the desktop environment.  It's a program.

If I'm remembering right, the default in Lubuntu is [FONT=Courier New]scrot[/FONT] which you can also run from a Terminal -
```
scrot -s
```
If you prefer something with a GUI, there are other "snipping tool" type screenshot programs available in the Ubuntu repositories, e.g. gnome-screenshot.

wow gnome screenshot was already installed, thanks!

but how do i add this to the programs tasbar?

---

### Post by ajgreeny on 2018-10-20
I have no idea how well, or even if it will work in Lubuntu without pulling in the complete xfce4 desktop, but xfce4-screenshooter allows you to save either the whole screen, the active window or crop to an area defined by dragging the mouse-cursor.

It might be worth trying as I know other xfce4 applications work well in Lubuntu, eg, xfce4-power-manager, which I think is still the default.

I have set keyboard shortcuts for all three, printscreen alone or with Alt or Winkey depending on which I want.

---

### Post by Dennis N on 2018-10-20
> In windows there is an image snipping tool which lets you select an area of the screen and save that as an image instead of you having to do a print screen of the entire screen and then have to paste into an image program for saving, **is there one like this for lubuntu?**

Newest Lubuntu 18.10 has a screen shot application with a GUI in default installation - has options for whole screen, window, or selected area. It's under **Menu > Graphics** category.

P.S. It's called Screenshot, but it's not Gnome Screenshot (which is not installed).

---

### Post by him610 on 2018-10-20
On Xubuntu, the default screenshot is > xfce4-screenshooter

---

### Post by again? on 2018-10-21
By default Lubuntu uses scrot.
You can alter the bound shortcuts in the lubuntu-rc.xml file.

First create a backup.
```
cp ~/.config/openbox/lubuntu-rc.xml ~/.config/openbox/lubuntu-rc.xml.bak
```

Edit lubuntu-rc.xml...
```
leafpad ~/.config/openbox/lubuntu-rc.xml
```

Search for "print" and you'll find a section as in pic.
[ATTACH=CONFIG]281395[/ATTACH]
Change **lxsession-default screenshot** to
```
sh -c "scrot [COLOR="#FF0000"]~/Pictures/screenshots[/COLOR]/$(date +%Y%M%d%H%m%S).png"
```

Change **lxsession-default screenshot window** to
```
sh -c "scrot -s -b -d1 [COLOR="#FF0000"]~/Pictures/screenshots[/COLOR]/$(date +%Y%M%d%H%m%S).png"
```
Create a ~/Pictures/screenshots directory or change above for [COLOR="#FF0000"]your screenshots location[/COLOR]
After edit...
[ATTACH=CONFIG]281397[/ATTACH]

Reload the window manager....
```
openbox --reconfigure
```

Test keys Print(fullscreen) and alt+Print(selection).

When using alt+print a left mouse click will select window or 
hold down left mouse and draw a selection rectangle and release.

If you want to revert the changes...
```
cp ~/.config/openbox/lubuntu-rc.xml.bak ~/.config/openbox/lubuntu-rc.xml
```

---

