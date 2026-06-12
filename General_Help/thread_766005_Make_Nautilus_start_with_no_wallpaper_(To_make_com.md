---
title: "Make Nautilus start with no wallpaper? (To make compiz' wallpaper plugin work)"
date: 2008-04-24
forum: General Help
---

### Post by Fireblend on 2008-04-24
Hey, I need some help making Compiz' wallpaper plugin work. It seems to work, but the Nautilus background is in the way; I already unselected the "Show Background" box on gconf-editor but it still loads the background image even when I kill it and start it with --no-desktop.

Any help would be greatly appreciated, thanks in advance!

---

### Post by gcurchod on 2008-09-09
Hello,

You can make this happen in the menu *System>Preferences>Sessions*.
In *Startup Programs* section, edit *Nautilus* and add **--no-desktop** to the *Command* option.

It should work after reloging. :-)

If you want to keep your icons, you can take a look here: [http://forum.compiz-fusion.org/showthread.php?t=6199]("http://forum.compiz-fusion.org/showthread.php?t=6199")

---

### Post by billgoldberg on 2008-09-10
This would be better done using gconf-editor (launch it from alt+f2).

I believe you need to un-select "apps -> nautilus -> preferences -> show_desktop".

This is from the top of my head, so I could be wrong, but it's somewhere in there.

I'm sure google will tell you exactly.

I would googlde "compiz fusion wallpaper plugin gconf-editor"

---

### Post by Shpongle on 2009-10-18
thanks been lookin for this for a while

---

