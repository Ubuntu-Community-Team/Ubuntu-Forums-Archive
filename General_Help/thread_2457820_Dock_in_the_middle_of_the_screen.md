---
title: "Dock in the middle of the screen"
date: 2021-02-10
forum: General Help
---

### Post by lastdanz on 2021-02-10
Namaste fellows! 

I'm using a new monitor, and I have this weird behaviour: the dock goes to the middle of the screen (please, see the attached screen-capture)
Even though I change the dock-position in dconf, it doesn't move. I've des/connected the monitor from the computer a pair of times, and restart/shut down the computer as well.
Please, may you be so gentle to help me? Thanks a lot in advance!

---

### Post by deadflowr on 2021-02-10
It's not the dock, it's the panel and has no setting to change it in dconf.
Look at how your display setting is setup in Setting >> Display.

---

### Post by ajgreeny on 2021-02-10
Is that the gnome desktop of Ubuntu or some other DE?

I do  not use the default gnome but what happens if you right click in the panel; do you get preference options to configure the panel as there are in  most other DEs that allow you to drag it where you want?

---

### Post by deadflowr on 2021-02-10
> **ajgreeny said:**
> Is that the gnome desktop of Ubuntu or some other DE?

I do  not use the default gnome but what happens if you right click in the panel; do you get preference options to configure the panel as there are in  most other DEs that allow you to drag it where you want?

Yes, it's gnome shell.
But there is no easy  preferences setting for it.
The panel is set by the gnome shell theme and configurations.

Two ways to manipulate it are 
1) painstaking editing of the shell theme, which is unbearable.

2) use of a shell extension, which looking at it closer, is what they might have enabled.
(I notice the clock in the off kiltered panel is toward the right side, instead of the default center,

Perhaps they have dock-to-panel or another extension like that installed and enabled.
In which case, perhaps check the extension settings for it.

---

### Post by lastdanz on 2021-02-11
Thanks for your reply! Looking for "panel", I could install Tweaks, and therefore dash-to-panel, so I could change the set up, and now the panel is completely in the bottom of the desktop! Hurray!
But, on the other hand, I've lost the dock :lolflag:
I've tried to enable the Ubuntu dock in Tweaks, but it doesn't. If you have any suggestion on this...

Thanks again!

---

### Post by Dennis N on 2021-02-11
**dash to dock** or **dash to panel** replaces the Ubuntu dock. You can't use Ubuntu's default dock with either of those extensions.

Update: See Post #8

---

### Post by lastdanz on 2021-02-11
I can't even install dash to dock..

---

### Post by Dennis N on 2021-02-11
> **lastdanz said:**
> I can't even install dash to dock..

What I said about having only one of dash to panel or dash to dock was mistaken. I thought that was the case, but I just tried it and found it does work. See the screenshot.  Dash to dock can be on any edge of the screen as well.

---

### Post by deadflowr on 2021-02-11
It's been a while but once upon a time I had both dash to dock ad Ubuntu dock installed and enabled,
and while they share most things, and it could be hard to tell they were both enabled, 
it did produce a slight ghosting-like effect whenever I did something  that triggered them.
(Like I set the dock to intellihide and if i hovered the mouse over it, the dock would appear,
but when I moved to mouse one would move back into hiding but the other kind of sat there for a moment then hide)

That was a different lifetime, coming close to 3 years ago and different hardware.
So I wouldn't be surprised if things changed.

---

