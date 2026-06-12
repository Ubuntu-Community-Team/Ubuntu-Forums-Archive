---
title: "Setting window positions with wmctrl"
date: 2015-02-08
forum: General Help
---

### Post by texpat on 2015-02-08
This is on Xubuntu 14.04.1 LTS

I'm trying to automate certain aspects of my work setup, where I use several different apps and want them distributed over my screen real estate in a certain way.

I've found [FONT=Courier New]**wmctrl**[/FONT] and some example scripts that use it. Unfortunately wmctrl is very erratic and will sometimes work and sometimes not, which is obviously very frustrating.

So I'm looking for help: Is there a way to make wmctrl work properly? Are there alternatives? What do others do in my situation?

---

### Post by kerry_s on 2015-02-08
well xfwm is probably fighting you on placement. it has a setting in window tweaks for placement, try turning that all the way up so it only affects large windows.

---

### Post by texpat on 2015-02-08
kerry_s: Yes, I had the suspicion there may be a conflict there somewhere, but it seems wmctrl still looses out after applying your tweak.

---

### Post by kerry_s on 2015-02-08
sure it's not your script ?
can you go in to more detail on what your trying to do ? pic maybe ?

---

### Post by texpat on 2015-02-08
Sure, here's screenshot of what I'm trying to do:

Left two windows go on one screen. The right window goes on another.

[ATTACH=CONFIG]259840[/ATTACH]

Here's an example script I'm using:

```
#!/bin/bash
function get_window_id()
{
window_id=$(wmctrl -l | grep "$1" | tail -1 | cut -f1 -d" ")
}

firefox -new-window "website.html"
get_window_id "Mozilla Firefox"
wmctrl -i -r "$window_id" -e 0,0,0,950,1080

firefox -new-window "other-webseite.html"
get_window_id "Mozilla Firefox"
wmctrl -i -r "$window_id" -e 0,950,0,968,1080

libreoffice --writer "textdoc"
```

I don't actually use wmctrl on the last window because the window manager places it where I want it.

---

### Post by dragonfly41 on 2015-02-08
There is also Window Master .. Firefox Add-on

[https://addons.mozilla.org/en-US/firefox/addon/monitor-master/](https://addons.mozilla.org/en-US/firefox/addon/monitor-master/)

---

### Post by kerry_s on 2015-02-08
maybe you should look into tiling wm's, xfwm4 can easily be replaced. while still keeping everything else. just a thought.

---

### Post by Toz on 2015-02-08
I use [devilspie]("http://www.foosel.org/linux/devilspie") when I want to place apps in specific locations.

Also: [https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")

---

### Post by CantankRus on 2015-02-08
I find binding xdotool and wmctrl commands  to easystroke mouse gestures invaluable.
All you need do is draw the gesture on the window you want the command to act on.
All I change in easystoke is the gesture button from 2 to 3. Feels more natural using the right mouse button.

---

### Post by texpat on 2015-02-10
> **kerry_s said:**
> maybe you should look into tiling wm's, xfwm4 can easily be replaced. while still keeping everything else. just a thought.

I played around with Awesome a while ago. Perhaps its time to give it another go.

> **Toz said:**
> I use [devilspie]("http://www.foosel.org/linux/devilspie") when I want to place apps in specific locations.

Had a quick look at that, too. But it doesn't seem to be what I'm looking for. I want a command to bring up and position app windows. This seems to apply a default behaviour to app windows when they appear. This is not quite what I'm after. I'll have a closer look at that link you gave, though. Thanks!

> **CantankRus said:**
> I find binding xdotool and wmctrl commands  to easystroke mouse gestures invaluable.
All you need do is draw the gesture on the window you want the command to act on.
All I change in easystoke is the gesture button from 2 to 3. Feels more natural using the right mouse button.

This is novel to me. Looks like it could be worth a try. Thanks!

---

