---
title: "Can you enable/disable Composite &quot;on demand&quot;?"
date: 2008-04-26
forum: General Help
---

### Post by SB-X on 2008-04-26
The XFWM and Ubuntu Appearance settings let you switch Composite on or off at runtime. How does this work? I can see that the WM has to be restarted, but does the WM have to do this via some X library call or is there some simple  command you can run?
Would it be possible to write a C program to toggle it? I don't know anything about X programming.

What I'd like to do is set up a panel button to toggle compositing effects on or off for when I run a game or something.
Instead of the above method I guess one could write a script to change the compositing setting, kill the WM, and restart it. Then they could just run the script from a panel launcher.

---

### Post by AndyCR on 2008-04-26
The easiest way I know is:

To kill:

```
killall compiz.real
```

Which may have to be followed with && yourwinmanager, IE:

```
killall compiz.real && metacity
```

To start:

```
compiz --replace
```

If all you want is a toggle button, this -should- work (untested):

```

#! /bin/bash

pstree | grep compiz.real > /dev/null
if [ $? -eq 0 ]; then killall compiz.real; else compiz --replace; fi

```

File properties, permissions, allow executing file as a program. Place it somewhere under your home folder (IE /home/yourname/toggle.sh), then create a panel button with a command of /home/yourname/toggle.sh.

---

### Post by scradock on 2008-04-27
The easy way is to install fusion-icon. This sits as a panel icon ready to turn compiz off or on, or to switch decoration manager as you wish. It's in the repos; for some reason it has warnings about being un-authenticated, but it seems to work fine - looks like a good solid python program.

sudo apt-get install fusion-icon 

should do it. Then you may have to launch it from the Applications | System Tools menu, and you can set it up to run as an autostart in the sessions menu.

---

### Post by SB-X on 2008-04-29
@AndyCR: That's something like I imagined, although I'm starting to like XFWM now. It's so light and - with composite enabled - even faster than Metacity. It does transparency which is the only effect I cared about.
I recommend it. For a modest setup like mine a lighter DE makes everything more responsive. (although I'm still using the Gnome panel along with XFCE because my launchers are there and I'm too lazy to move them)

@scradock: Gutsy? I don't see it with apt-get/apt-cache/apt-file. Maybe that's why it's saying unauthenticated. ;)

Thank you both for the advice.

---

### Post by chalewa on 2008-05-03
> **AndyCR said:**
> The easiest way I know is:

To kill:

```
killall compiz.real
```

Which may have to be followed with && yourwinmanager, IE:

```
killall compiz.real && metacity
```

To start:

```
compiz --replace
```

If all you want is a toggle button, this -should- work (untested):

```

#! /bin/bash

pstree | grep compiz.real > /dev/null
if [ $? -eq 0 ]; then killall compiz.real; else compiz --replace; fi

```

File properties, permissions, allow executing file as a program. Place it somewhere under your home folder (IE /home/yourname/toggle.sh), then create a panel button with a command of /home/yourname/toggle.sh.


this works really well...but when i turn off compiz, how do i edit that script to allow metacity to start then?

---

