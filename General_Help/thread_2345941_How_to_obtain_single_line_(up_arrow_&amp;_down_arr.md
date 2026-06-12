---
title: "How to obtain single line (up arrow &amp; down arrows) scrolling in the desktop"
date: 2016-12-09
forum: General Help
---

### Post by multibot on 2016-12-09
This seems impossible in both system settings and the unity tweak tool, and the three installed themes lack this (Ubuntu 16.04). 

Anyway I would like to fix this at the "whole" desktop level if possible, and the thread [https://ubuntuforums.org/showthread.php?t=1965929]("https://ubuntuforums.org/showthread.php?t=1965929")  indicates changing config files as follows:[INDENT]... put the following in the ~/.gtkrc-2.0 file:

style "default" {
  engine "murrine" {
    stepperstyle = 0
  }
}

and the following into the file ~/.config/gtk-3.0/gtk.css:

.scrollbar {
  -GtkScrollbar-has-backward-stepper: 1;
  -GtkScrollbar-has-forward-stepper: 1;
}

I needed to at least log out and log in to get the steppers to appear.  Once I had to do a complete reboot.
[/INDENT]


However I do not have these two files. Presumably things have moved on since a couple of years ago (or it's because that solution was for Xubuntu).

Is there a similar config files method to get single scrolling that I can use now please ? Thanks.

- - - - 
For the curious as to why: I very much want this since my right hand fingers have gone numb and sore from key presses and also continuously holding mouse left to scroll. Also ordinary scroll is way too inaccurate for long documents or webpages.

---

### Post by vasa1 on 2016-12-09
> **multibot said:**
> This seems impossible in both system settings and the unity tweak tool, and the three installed themes lack this (Ubuntu 16.04). 

...However I do not have these two files. Presumably things have moved on since a couple of years ago (or it's because that solution was for Xubuntu).

Which three installed themes? At least Ambiance "lacks this" only by default. I think you can get those very tiny arrows at the very top and bottom of the scrollbar if you do something like this:

First back up the theme you want to change as a precaution.
Run```
sudo -H gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```
Change```
stepperstyle = 3
```to```
stepperstyle = 1
```and save the file.

Run```
sudo -H gedit /usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css
```
Change```
    -GtkScrollbar-has-backward-stepper: 0;
    -GtkScrollbar-has-forward-stepper: 0;

```
to
```
    -GtkScrollbar-has-backward-stepper: 1;
    -GtkScrollbar-has-forward-stepper: 1;

```and save the file.

You may also want to modify */etc/gtk-3.0/settings.ini* by adding ```
gtk-primary-button-warps-slider=false
```to the end of it to get "legacy" scrolling.

After making the changes, switch to another theme and then back to Ambiance. That should be enough to get the changes to register. If not, log out and log back in.

---

### Post by multibot on 2016-12-12
Thanks for that vasa1, and apologies for not replying sooner; very useful!

---

### Post by vasa1 on 2016-12-12
> **multibot said:**
> Thanks for that vasa1, and apologies for not replying sooner; very useful!

You're welcome and, if you wish, you can mark the thread [SOLVED] as described here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

