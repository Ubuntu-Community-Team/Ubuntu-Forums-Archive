---
title: "What do these scrolling options in gnome-terminal mean?"
date: 2016-03-17
forum: General Help
---

### Post by vasa1 on 2016-03-17
```
$ apt-cache policy gnome-terminal
gnome-terminal:
  Installed: 3.6.2-0ubuntu1
  Candidate: 3.6.2-0ubuntu1
  Version table:
 *** 3.6.2-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```Can someone please explain what[LIST]
[*]Scroll on output
[*]Scroll on keystroke
[*]Use keystrokes to scroll on alternate screen
[/LIST]mean?

---

### Post by Nutster on 2016-03-17
All of these relate to what happens when you have scrolled up to see things that have already appeared on your console screen.  If certain activity occurs, the console will scroll to the bottom to show this new stuff.
"Scroll on Output" - When the program that is running in the console outputs something, scroll to make sure that the user can see it, usually down at the bottom.
"Scroll on Keystroke" - When the user types something, scroll the console so that the insertion point (this is where your keystrokes show up on the console) is visible.
I think "Use keystrokes to scroll on alternate screen" is a mistranslation or something like that.  It really seems to refer to using the scroll wheel on your mouse to make the console scroll.

In general, I would leave all of these on, unless you accidentally hit the mouse wheel too often, then turn off the last one.

---

### Post by vasa1 on 2016-04-07
After using gnome-terminal for a couple of weeks, I'm comfortable with just leaving "scroll on keystroke" checked.

I don't need "scroll on output" checked.

BTW, in the latest 16.04 image, the relevant screen is somewhat reordered. This is what the default looks like:

---

### Post by Bronsano on 2016-04-08
Kinds confusing

---

