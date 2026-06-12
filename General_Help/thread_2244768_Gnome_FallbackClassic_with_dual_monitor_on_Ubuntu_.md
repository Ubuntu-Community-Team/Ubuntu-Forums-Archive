---
title: "Gnome Fallback/Classic with dual monitor on Ubuntu 14.04"
date: 2014-09-18
forum: General Help
---

### Post by GouZi on 2014-09-18
[SIZE=4]Introduction
[/SIZE]

The Unity experience if you have more than one screen is still far from optimal in Ubuntu 14.04:
1. You have a duplicate unity panel on each screen (which can be removed in Preferences > Display > Launcher Placement).
2. You don't have a bottom panel with the Window list. Working often with a lot of windows open, the Unity window switcher is rapidly un-readable. I already hear, why do you have so many windows open? For good or bad, that's the way I like it and hey you have to fill up those screens with something, right? ;). This can be mitigated on 14.04 installing tint2 (sudo apt-get install tint2).
3. The top panel is duplicated on each screen and if you have some indicators (a la indicator-multiload), well, they'll be duplicated too: so you end up with 2 clocks, 2 sets of indicators, which looks pretty bad.

While 1. can be fixed and 2. has a workaround, so far I haven't been able to do anything about 3.... Please feel free to share if you have a workaround!

To customize the desktop experience, I fall back to well, gnome-session-fallback.

[SIZE=4]I. Install gnome-session-fallback
[/SIZE]

```
sudo apt-get install gnome-session-fallback

```
Log out, log back in chosing Gnome Classic (compiz).

Add a bottom panel on the right screen

```
Super + Alt + right click on the bottom panel > New Panel
```

Move it to the bottom of the right screen:
```
Super + Alt + left click and move it.
```

Add window list to the panel:
```
Super + Alt + right click on the bottom panel > Add To Panel > Window List.

```

At this point you have a bottom task bar on both screens and moving a window from one screen to another will also move its representation from the task bar on one screen to the other.

[SIZE=4]II. Add Virtual Worspaces
[/SIZE]

Even with 2 screen you may want to add virtual workspace, to do so:

```
sudo apt-get install compizconfig-settings-manager

```
Then go to:

```
Appications -> System Tools -> Preferences -> CompizConfig
> General > Desktop Size > horizontal:2, vertical: 2

```

[SIZE=4]III. Application switcher
[/SIZE]

You might notice that Alt + Tab does not work. To make it work:

```
sudo apt-get install compiz-plugins-extra
```

Then go to:
```
Appications -> System Tools -> Preferences -> CompizConfig
> Window Management > select: (Static) Application Switcher

```

[SIZE=4]Conclusion
[/SIZE]

It's too bad unity does not offer the ability to have the top panel in only one screen or at least not have all the indicator duplicated across screens. Gnome Fallback/Classic can get your there, but it's not without a few tricks...

---

