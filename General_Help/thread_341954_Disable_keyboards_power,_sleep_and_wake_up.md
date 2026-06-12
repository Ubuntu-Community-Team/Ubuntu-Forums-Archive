---
title: "Disable keyboards power, sleep and wake up"
date: 2007-01-19
forum: General Help
---

### Post by andyrobo60 on 2007-01-19
Is there a way for me to disable the power, sleep and wake up buttons at the top of my keyboard. I have looked around and not found any help.

Any help I could get would be very much appreciated.

---

### Post by kebes on 2007-01-19
Well there is a linux command called "[xmodmap]("http://www.xfree86.org/4.2.0/xmodmap.1.html")" that lets you redirect arbitary keys. You could write a script that redirects those keys to nowhere, so that they don't do anything. Then set the script to autorun when gnome/kde starts up.


1. First you would run (install if required) a program called "xev" which lets you determine the keycodes for key-events. Basically it's a little window and when you press a key it will show you the keycode for it. (Er... this might be difficult to do if the sleep key actually puts your computer to sleep! You may be able to get the key-codes another way...)


2. Then you create a simple script that runs xmodmap. Usage is like this:
xmodmap -e 'keycode <keycode from xev>=<key output>'

So you could re-assign those keys to do nothing or to map to other keys if you prefer (use them as neat function keys if you want!).

You would end up with a script like:
```

#!/bin/bash
xmodmap -e 'keycode 231=F1'
xmodmap -e 'keycode 232=F2'
xmodmap -e 'keycode 233=F3'

```
Then you make the script executable:
chmod +x keycodes

Try running it:
./keycodes

And see if the keys are re-assigned as you wanted them.


3. If it works, set the script to autostart. In KDE you would put a copy in:
/home/username/.kde/Autostart/
(I'm sure there's a way to do it in Gnome, too.)



Hope that helps.

P.S.: you can also do things like:
xmodmap -e 'keycode 160=XF86AudioMute'
to re-map keys to certain X functions. You can also do this to manually enable special keys that are on some keyboards/laptops.

---

