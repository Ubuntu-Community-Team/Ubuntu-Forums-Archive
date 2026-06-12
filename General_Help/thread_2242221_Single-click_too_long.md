---
title: "Single-click too long?"
date: 2014-08-31
forum: General Help
---

### Post by 2CV67 on 2014-08-31
Although I am right-handed, I use a right-handed mouse with my left hand (..it's a long story).

In the past, the only problem has been with double-click speed.
since I am double-clicking with my non-prefered hand & with my middle finger, the response rate is slow, so I always have to set double-click speed to fairly slow.

Now, with my latest-&-greatest new PC with 14.04 Unity, I have hit a new problem.
Single-clicking sometimes does not work!
After some experimenting, it seems that the problem is due, again, to slow response.
I am holding the left button down for a little too long.
If I try very hard, I can single-click-&-release relatively fast & then there is no problem.
If I don't concentrate, then all sorts of errors occur, due to audible clicks not being actioned.

I thought the problem might be related to the new (cheapo-feeling) Acer mouse which came with the PC, so went back to my trusty old MS mouse which I have used for years - and I get the same problem.

Is this a known problem?

Is there a known solution?
I thought there might be some related setting for handicapped people, but didn't see anything.

Thanks!

---

### Post by 2CV67 on 2014-09-04
Bump...

Surely there has to be a value somewhere for the minimum dwell-time considered as click-&-hold?

I did a lot of browsing & searched through compiz & tweaks etc, without finding anything yet...

Thanks for any pointers!

---

### Post by 2CV67 on 2014-10-31
Re-bump!

This is a nuisance.

I have W8 on the same PC with the same mouse(s) and that works perfectly.
Everything reacts crisply to either the beginning or the end of a single click, even if that click is held for well over a second.
Just as you would expect.

Back in Ubuntu, back in trouble...
If I single-click on a tile from the launcher, holding the click maybe one-tenth of a second (can't measure it) then the tile just wobbles a bit, as though I wanted to move it.
If I single-click on a window menu item (I have menus on windows) for longer than one-tenth of a second, then the menu does not open & the window title appears briefly.

Obviously (I think!) the threshold time between single-click and click-&-hold is set to some ridiculously short time around one-tenth of a second.
And I can't find out where this setting is stored or how to change it.

Surely I am not the only user with this concern?

I suppose I will raise a Bug Report.

---

### Post by ibjsb4 on 2014-10-31
Hi 2CV67

Have you tried playing with dconf-tools?
[ATTACH=CONFIG]257641[/ATTACH]

---

### Post by 2CV67 on 2014-10-31
I have used dconf-editor for other tasks, but had not found the mouse section you point out - thanks!

But when I look at that window in detail, I don't think anything there covers my problem, does it?

Maybe I can find something else in there...

---

### Post by 2CV67 on 2014-10-31
Going on from your suggestion - in terminal, I tried ```
gsettings list-schemas | grep -i mouse

```
That brought up:
```
org.gnome.desktop.a11y.mouse
org.gnome.mousetweaks
org.gnome.settings-daemon.plugins.mouse
org.gnome.settings-daemon.peripherals.mouse
```

In dconf-editor, I located all the above except mousetweaks, but I couldn't find anything related to my problem.

I don't know what/where mousetweaks is or whether it might help.

---

### Post by CantankRus on 2014-10-31
If I am opening a folder I have to hold down the button a full second before the release is not recognized.

---

### Post by 2CV67 on 2014-11-01
Thanks for that input!

Opening folders for me is a double-click affair, so unrelated to my problem.

But I am VERY interested to know how your (& everybody else's) single-click works when used, say, on a Tile in Launcher.
If I click-&-hold near the corner of a tile, the tile jumps towards where I click (Ready to be moved in the Launcher) & does not open the Application, even when I release it.
If I click & release very very quickly, it opens the application OK.
Now my problem is that if I click & release "normally" (holding maybe 0.2 seconds??) then the tile jumps & the Application is not opened.

I understand why there has to be this difference in behaviour between click-&-release and click-&-hold.
I understand that setting the threshold time between the 2 is a compromise & the compromise may not be good for everybody.
But I don't understand why I can't find & modify that threshold value.

---

### Post by vasa1 on 2014-11-01
For gtk2, see if the post by Frank helps: [http://forum.lxde.org/viewtopic.php?f=8&t=501#p1720](http://forum.lxde.org/viewtopic.php?f=8&t=501#p1720)

I think the same code in gtk3's settings.ini should work too. There's "gtk-long-press-time" as well.
Source: [https://developer.gnome.org/gtk3/stable/GtkSettings.html](https://developer.gnome.org/gtk3/stable/GtkSettings.html)

I use Openbox and the number of milliseconds between clicks to register as a double-click on the title bar can be set. Maybe your WM has something similar.

---

### Post by CantankRus on 2014-11-01
I think the unity launcher behaviour is a setting unto itself.
Maybe use middle click where there is no timeout or get used to tapping like a fire button instead of clicking.

---

### Post by 2CV67 on 2014-11-01
> **vasa1 said:**
> For gtk2, see if the post by Frank helps: [http://forum.lxde.org/viewtopic.php?f=8&t=501#p1720](http://forum.lxde.org/viewtopic.php?f=8&t=501#p1720)

I think the same code in gtk3's settings.ini should work too. There's "gtk-long-press-time" as well.

You got my interest, but...

My home directory has no hidden .gtkrc files.

When I look for any gtk settings.ini files, I find:
/etc/gtk-3.0/settings.ini 
/user/share/themes/Ambiance/gtk-3.0/settings.ini
/user/share/themes/HighContrast/gtk-3.0/settings.ini
/user/share/themes/Radiance/gtk-3.0/settings.ini

None of these has anything about mouse in it.

---

### Post by 2CV67 on 2014-11-01
> **CantankRus said:**
> Maybe use middle click where there is no timeout or get used to tapping like a fire button instead of clicking.

Yes - I am trying to learn to tap sharply, but it is not easy & I would prefer to alter a setting, once & for all!

Middle-click works on the Launcher for launching an app but not for toggling it back (option I find essential).
Also does not work on window menus - it sends the window to the back...

---

### Post by vasa1 on 2014-11-02
> **2CV67 said:**
> You got my interest, but...

My home directory has no hidden .gtkrc files.

When I look for any gtk settings.ini files, I find:
/etc/gtk-3.0/settings.ini 
/user/share/themes/Ambiance/gtk-3.0/settings.ini
/user/share/themes/HighContrast/gtk-3.0/settings.ini
/user/share/themes/Radiance/gtk-3.0/settings.ini

None of these has anything about mouse in it.
It's likely that your issue is something I don't know about, but please take a look at [Adjusting the mouse double-click for gtk apps]("http://ubuntuforums.org/showthread.php?t=2251095")

---

### Post by 2CV67 on 2014-12-01
Well - bump...

Surely there HAS to be a threshold value set somewhere to distinguish between click-&-release and click-&-hold?
If only for the Unity Launcher tiles & Window Menus, where the difference in response between click-&-release and click-&-hold is radical.

---

