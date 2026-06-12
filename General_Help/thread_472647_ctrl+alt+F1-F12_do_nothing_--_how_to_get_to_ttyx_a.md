---
title: "ctrl+alt+F1-F12 do nothing -- how to get to ttyx and start multiple X servers"
date: 2007-06-13
forum: General Help
---

### Post by 1veedo on 2007-06-13
Never have I seen a distro of Linux that disabled your ability to use the ttys (whatever they're called).  ctrl+alt+F1-F6 always brings up a console.  F7+ is for multiple X servers.  Like you can xinit somegame -- :2 and you have your desktop at F7 and the game at F8 so you can switch between the two.

How do you do this in Ubuntu?  I altered a couple config files just searching for the errors of xinit but I still cant get it working.  I even turned off gdm.  When Ubuntu boots I see a console but after I startx I cant get back to the console.  Totally annoying -- I figure the developers did this so users wouldn't see anything "weird" but all they did was reduce the functionality of Ubuntu.  The ability to run multiple X servers is one of the more useful things you can do w/ Linux that you cant do with Windows.

---

### Post by MikePiff on 2007-06-13
Strange!  I can get F1 to F7 working but am stumped on F8.  I just get a cursor top of screen with that one, unless I do a new session after first login!  You would think it would be possible just to press Ctrl Alt F8 and get a new login screen?

---

### Post by birdmun on 2007-06-13
ctrl+alt+F7-F12 are typically reserved for xservers as F1-F6 are typically for consoles
The reason therefore that F8 was only a cursor is because you didn't have an xserver running on that space. If you ctrl+alt+F2-F6 you should have access to consoles and be able to login and start multiple Xwindow sessions.

---

### Post by 1veedo on 2007-06-13
> **birdmun said:**
> ctrl+alt+F7-F12 are typically reserved for xservers as F1-F6 are typically for consoles
The reason therefore that F8 was only a cursor is because you didn't have an xserver running on that space. If you ctrl+alt+F2-F6 you should have access to consoles and be able to login and start multiple Xwindow sessions.Yes so why is it that Ubuntu, and as far as I can tell only Ubuntu, limits access to these consoles and the ability to run multiple X servers?  It only runs the desktop and wont allow you to ctrl+alt+F1-F6; it just goes to a blank screen.

---

### Post by Khaled Khalil on 2007-06-13
1veedo, this is not the normal behaviour in ubuntu, i should work like it did always.
however, me too i have the same issue since this morning, i am checking for possible solution

i found also [this post]("http://ubuntuforums.org/showthread.php?t=472825") about the same problem, if somebody suggested a solution in a post i will link it to the other one

---

### Post by hardyn on 2007-06-13
If you are using the binary nvidia drive, i believe this is a known problem.

---

### Post by Khaled Khalil on 2007-06-13
[QUOTE=hardyn]If you are using the binary nvidia drive, i believe this is a known problem.[/QUOTE]
for me yes, i am using it, but that's since long time ago when i installed Ubuntu.
this problem just began today !
also it is related to tty terminals, not only X server (actualy i can still run multiple X servers through "sudo X :1 -ac" but can't return back, i had to kill it with ctrl+alt+back_space)
may be it is just the keybindings !, but which key binding ? it is not related to the window manager, neither the X server (ctrl+alt+backspace works)
any idea ?
without ttys nor multiple X severs i feel i am on windoz :(

---

### Post by donheff on 2007-06-13
Alright, curiosity killed the cat.  I use Linux to run my family webserver and recently switched to Ubuntu.  I always manage the servers thru VNC (Vino with Ubuntu since I can't get VNC working properly).  In any event, I never used ctlr alt F1-F8 and wasn't familiar with the functionality.  You folks got me curious so I keyed in ctrl alt F1 (on the remote keyboard).  My screen went black so I went down in the basement and hooked up a monitor.  I was at a command line login screen.  I logged in and keyed in startx.  I was informed that a X session was already running on :0.  So what happened to my x session?  And what do F2-F8 do?

---

### Post by 1veedo on 2007-06-13
> **Khaled Khalil said:**
> without ttys nor multiple X severs i feel i am on windoz :(Lol I feel trapped to my desktop.  It's very distressing especially considering that I cant switch between a fullscreen game and my desktop.  The entire reason I decided to post about this problem was because I wanted to run enemy territory in a seperate X server so I could reference a website giving instructions to boost your fps.  I dont know what Windows people do; I guess they open and close fullscreen apps or maybe they memorize all the commands ahead of time.[quote=donheff]Alright, curiosity killed the cat. I use Linux to run my family webserver and recently switched to Ubuntu. I always manage the servers thru VNC (Vino with Ubuntu since I can't get VNC working properly). In any event, I never used ctlr alt F1-F8 and wasn't familiar with the functionality. You folks got me curious so I keyed in ctrl alt F1 (on the remote keyboard). My screen went black so I went down in the basement and hooked up a monitor. I was at a command line login screen. I logged in and keyed in startx. I was informed that a X session was already running on :0. So what happened to my x session? And what do F2-F8 do?[/quote]The other X session is still there, just ctrl+alt+F7 to get back to it.

If you want to start another X server you have to give it a new address: startx -- :1.  You can also use xinit someapp like xinit /usr/bin/someapp -- :XX.  The X servers are on the F7+ keys.

---

### Post by Khaled Khalil on 2007-06-15
\\:D/ at last i solved it
just reinstall "xkb-data" and restart

i knew this by concidence, (after uninstalling every recent installation(that didn't help solving this)) i noticed that the keyboard layout doesn't change, so from "keyboard preferences"->"layout option"->every single change popup 2 identical error messages:
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
so i reinstalled those packages and restarted, next login a popup error said that (i didn't save the text) while X was starting it didn't find "rules/xorg", so i said xorg rules, i searched in [ubuntu packages]("http://packages.ubuntu.com/") about any package containing any file or directory name like "rules/xorg", and "xkb-data" is what i found, so i reinstalled it, and now it works ;)

now i am back to life :D

---

### Post by whawes on 2008-01-10
I had the same problem described here while using gutsy on a laptop with a Nvidia GeForce Go 6600 and the nvidia driver. I tried the OP's suggestion but this did not work. After comparing my xorg.conf file with one on another similar laptop, I found that the non-functional one had one additional setting:

Option "XkbVariant" "gb"

and didn't have one setting present in the functional machine's config file:

Option      "XkbOptions"    "lv3:ralt_switch"

I removed the first one, added the second and rebooted and voila, problem fixed. Not sure which one solved it, perhaps someone can verify later.

HTH

---

