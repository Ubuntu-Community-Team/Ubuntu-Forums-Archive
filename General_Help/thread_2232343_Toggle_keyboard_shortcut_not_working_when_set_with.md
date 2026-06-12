---
title: "Toggle keyboard shortcut not working when set with setxkbmap"
date: 2014-07-01
forum: General Help
---

### Post by collinstocks on 2014-07-01
Hi all,

I'm setting the keyboard map on my laptop using:

```
setxkbmap -rules evdev -model pc104 -layout "us,us" -variant ",dvorak" -option "grp:alt_caps_toggle"
```

This should set up two keyboard layouts: us as the primary layout, and us:dvorak as the secondary layout. It also sets up a keyboard shortcut, alt-caps, to toggle between the two layouts.

This used to work until I upgraded to Ubuntu 14.04. Now the toggle doesn't work. The keyboard is just set to use the primary layout, and won't switch away from it to the secondary layout when I press alt-caps.

I have no idea how to investigate this, so any help would be much appreciated.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```

---

### Post by Rob Broccoli on 2014-07-10
I have almost the same problem:  I was using "setxbmap dvorak" after
I logged in, which would give me a dvorak layout for the duration of
my session.  After upgrading to Trusty, the command only seems to
work from a terminal and only applies to the terminal from which I
run it.  And worse yet, if I switch focus to a different application
(like a browser) and then back to the terminal, the keyboard reverts
to qwerty!  Even moving the window makes it revert, which makes me
think the window manager is the culprit.
  Because I'm running Xubuntu, the appropriate tool to set the keyboard
layout is "xfce4-keyboard-settings".  Except that it doesn't have any
effect.
  So I'm kinda screwed here until I figure this out or I relearn how
to use a qwerty keyboard.

 The window manager for Xubuntu is xfwm4. Do you know if that's what
you have too?  If so, that would be a hint to where the problem is.

---

### Post by collinstocks on 2014-07-10
I'm using xmonad as my window manager, so it's not that in my case. Any ideas? Bump......

---

### Post by Rob Broccoli on 2014-07-10
I found a solution.  On Xubuntu, there's a panel plugin for changing layouts.   It's called "xfce4-xkb-plugin" on Xubuntu, but if you click its "about" button, it calls itself "IBus".  It seems to do exactly what you wanted: set up a keyboard shortcut to switch between layouts.   Here's the website if you need it.  [https://code.google.com/p/ibus/](https://code.google.com/p/ibus/)

---

### Post by collinstocks on 2014-07-10
I installed xkb-switch, which should be able to switch the layout group with the -n option, but that doesn't work either. This isn't just a keyboard shortcut issue.

---

### Post by Rob Broccoli on 2014-07-10
Turns out that ibus was already installed on my system, and I'll wager that it was the ibus daemon that was superceding the setxkbmap settings.  From a terminal, try entering "ibus engine"  -- when I do it, I get
$ ibus engine
xkb:us:dvorak:eng

      If you don't have ibus installed, then we are probably looking at two different problems.  Sorry.

---

### Post by collinstocks on 2014-07-10
It appears I do have ibus installed.
Ibus engine gives
xkb:us::eng
Even though my xkbmap is set as us(Dvorak)

Don't mind the capitalization; I'm on my phone.

---

### Post by Rob Broccoli on 2014-07-10
So to get dvorak, you just need to enter
$ibus engine xkb:us:dvorak:eng
    and to get back to US qwerty
$ibus engine xkb:us::eng

       To toggle back and forth with a keyboard shortcut, the easiest way is with a plugin.  You probably have a panel plugin that will do it, I just don't know what it's called.  If not Ibus, then maybe Input Method Switcher or something like that.

---

### Post by Rob Broccoli on 2014-07-10
Alternatively, I find I can right-click on my terminal window and click on the "Input Methods" item (that I've been ignoring for years).   Click on "X Input Method" which de-selects System Ibus.  And then my old way of using "setxkbmap dvorak" works properly again.  
Sometimes I have to think real hard just to be stupid.

---

