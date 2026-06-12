---
title: "Windows key has stopped working"
date: 2007-10-25
forum: General Help
---

### Post by svivian on 2007-10-25
I used to be able to use the Windows key to control a couple of things like <Win>+C for Play/Pause Amarok. But it's stopped working now.

I think it happened after I ran xorg config (command: _sudo dpkg-reconfigure xserver-xorg_)
I've tried running it again and entering various settings for the keyboard, but it still doesn't work. And when I go to Prefs>Keyboard and try and change things I get this error message, which appears twice for each error:

```
Error activating XKB configuration.
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
```

My keyboard is a **Logitech Cordless Desktop EX110** and I'm running Ubuntu Feisty. (Also it should be set to 'uk' layout).

Here is a pic from amazon: [http://ecx.images-amazon.com/images/I/41ergULL5aL._SS400_.jpg](http://ecx.images-amazon.com/images/I/41ergULL5aL._SS400_.jpg)
Except my Windows key looks slightly different (not that it matters, heh).

Any ideas?

---

### Post by ezak on 2007-10-25
Try this, for your keyboard layout. Maybe your configuration/settings have changed somehow:

sudo dpkg-reconfigure console-data

---

### Post by svivian on 2007-10-25
> **ezak said:**
> Try this, for your keyboard layout. Maybe your configuration/settings have changed somehow:

sudo dpkg-reconfigure console-data

OK I ran that but it didn't make a difference, I still get that error on startup or when I try and change anything in keyboard prefs.

---

### Post by svivian on 2007-10-25
Ah, found the old xorg.conf backup that was created when I ran that reconfigure thing before. The only difference in the keyboard section was that the layout was "gb" rather than "uk", so changing it to "gb" worked a treat.

Now to set up lots of custom shortcuts...

---

### Post by svivian on 2007-10-25
OK another question - are there commands for showing the desktop and the 'shut down' dialog?
For example I wanna bind show desktop to <super>D in gconf-editor but I need a command...

---

### Post by ezak on 2007-10-25
Good to hear you got your keyboard fixed. 

Well it depends on the desktop you are running for keyboard shortcuts. For Ubuntu Gutsy by default, afaik, the shortcut to the "Shut Down" dialog is:

Ctrl+Alt+Delete  (Shut Down/Logout Menu)

For the "Show Desktop" shortcut, it's:

Ctrl+Alt+D  (Show Desktop)

Alternatively, you can also customize your shortcuts by navigating to:

System > Preferences > Keyboard Shortcuts

Hope that further helps you on getting your system just the way you like. If there are any more questions, feel free to ask away on the forums. That's how we all learn, from others, no matter if you are a SysAdmin or new user. :wink:

---

### Post by svivian on 2007-10-25
> **ezak said:**
> Well it depends on the desktop you are running for keyboard shortcuts. For Ubuntu Gutsy by default, afaik, the shortcut to the "Shut Down" dialog is:

Ctrl+Alt+Delete  (Shut Down/Logout Menu)

That's not working for me (Feisty). Any other ideas?

Cheers for the show desktop one though :)

---

