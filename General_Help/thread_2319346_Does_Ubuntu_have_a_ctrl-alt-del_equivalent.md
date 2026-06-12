---
title: "Does Ubuntu have a ctrl-alt-del equivalent?"
date: 2016-04-03
forum: General Help
---

### Post by ChristmasPi on 2016-04-03
This has happened a few times now where my Ubuntu 14.04 laptop has frozen up on me.  The last time was last night when I was watching a YouTube video in full screen.  The sound is still coming and my mouse moves, but my keyboard is locked and the video on screen is frozen.

On Windows, I can do a ctrl-alt-del and use task manager to close the browser and reopen it.

Is there a similar keystroke combination on Ubuntu?  My only option in the past has been to hard boot the PC and then sign back on.

Thank you

---

### Post by alex_32 on 2016-04-03
Ctrl+Alt+F1(F2,F3,F4 etc.)

This will open a shell, in which you can login as your account and type
```
kilall firefox
```

Then press Ctrl+Alt+F6 to go back to your desktop.

Note: on some distributions or desktop environments Ctrl+Alt+F1 is used to go back to the desktop, and Ctrl+Alt+F2(F3,F4,F5 etc.) are shells.

---

### Post by howefield on 2016-04-03
You could probably map a key combination to load gnome-system-monitor.

System Settings > Keyboard > Shortcuts

But, if your keyboard is really locked...

---

### Post by vasa1 on 2016-04-03
IIRC, it's possible to make an icon for *xkill* and stick that in a panel. If your mouse functions, you could click on the *xkill* icon and then kill the problematic window.

Bit old but maybe useful: [http://superuser.com/questions/456363/how-to-add-force-quit-icon-in-ubuntu-12-04](http://superuser.com/questions/456363/how-to-add-force-quit-icon-in-ubuntu-12-04)

I haven't tested it.

(For when your keyboard isn't locked up, you could use a keyboard shortcut to launch *xkill*. ajgreeny suggested *win*+*del* and that's what I've kept in case of emergency!

---

### Post by him610 on 2016-04-03
> my Ubuntu 14.04 laptop has frozen up on me

This the symptom of a problem that needs to be corrected; there is more of a load than the system can adequately handle. The system specs were not provided, but sometimes reducing  one's screen resolution will lighten the system load.

---

### Post by vasa1 on 2016-04-03
Is it only with Firefox or do other applications also cause the freeze?

PS: My OS, Lubuntu, uses ctrl+alt+del to bring up the task manager. I think other Ubuntu flavors use the same combo.

---

### Post by Bucky Ball on 2016-04-03
Don't know what the default key combination is to open a terminal in Ubuntu, but you could use that key combination then type:

> xkill

This will give you a cross cursor. Any app you click on will be killed immediately.

---

### Post by oldos2er on 2016-04-03
You can also use Alt-F2 to call xkill. On KDE Ctrl-Esc brings up a task manager; you can easily set your own hotkey combo to call your favorite system monitor/task manager or whatever you want to call it. I prefer htop.

---

### Post by sudodus on 2016-04-03
If you cannot do anything else, there is a soft shutdown, which is much better than a hard shutdown (pressing the power button for a long time).

I would recommend

[SIZE=3]***SysRq + r e i s u b***[/SIZE]

The hotkey combination for ***SysRq*** is often but not always ***alt + PrtScrn***.

Keep the hotkey combination for SysRq pressed, and press slowly each of the keys ***r e i s u b*** one after another. See this link for more information about the method

[Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by vasa1 on 2016-04-03
OP claims the keyboard becomes **unresponsive**. That's why I posted a "mouse"-based solution.

---

### Post by sudodus on 2016-04-04
Maybe your "mouse"-based solution is best in this case, *vasa1* :-)

Sometimes *SysRq + r e i s u b* works, even when the desktop environment is unresponsive. It is good to have many tools.

There is no response from the OP. Maybe they left long ago, maybe they are still waiting for a tip that works.

---

### Post by vasa1 on 2016-04-04
> **sudodus said:**
> Maybe your "mouse"-based solution is best in this case, *vasa1* :-)

Sometimes *SysRq + r e i s u b* works, even when the desktop environment is unresponsive. It is good to have many tools.

There is no response from the OP. Maybe they left long ago, maybe they are still waiting for a tip that works.
I'll wait till after 16.04 is out and you have some free time :)

I have a few questions about reisub.

---

### Post by sudodus on 2016-04-04
You can ask now, but I suggest that you create an own thread for it, and maybe link to it from here :-)

---

