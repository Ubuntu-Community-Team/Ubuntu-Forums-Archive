---
title: "Using X without a WM can't return to the console"
date: 2008-02-28
forum: General Help
---

### Post by ryanaligen on 2008-02-28
I'm trying to operate with console only for as much as possible.

However, when I do need GL applications I'd like to start X without the resource intensive window managers.

The idea is that I start X (type "X") and switch back to console 1 (alt+F1) to kick off the applications I want. I'm working with gparted for the tests.

What works:
1. Boot Ubuntu 7.10 from CD
2. Drop to run level 3
3. Execute X to start the X server without a WM

What doesn't work:
I can't switch back to console 1, 2, 3, etc!

Any help would be appreciated.

---

### Post by sumguy231 on 2008-02-28
That's weird 'cause you should be able to do that, but if you can at least get a terminal then you can issue a command for X to quit when you're done and it should dump you back to the console. I think your .xinitrc should look something like this:
```

#!/bin/sh
xterm (or any other X terminal you want to run goes here)

```

And when you're done with X you could probably run 'killall /usr/bin/X' or 'killlall X' to quit. As far as I know killall just TERMinates by default, it doesn't actually kill.

---

### Post by astrotech226 on 2008-02-28
I just tried this for giggles on my PC and it worked for me.  I didn't try it from the CD but from my harddrive.  There are a few differences on my setup though.  My runlevel default is two.  So I go to tty1 and do:

```
sudo /etc/init.d/gdm stop
```

Once there, I run "X" and get the gray screen as expected.  Ctl-alt-f1 and ctl-alt-f2 takes me back to the appropriate console screens.

---

### Post by sumguy231 on 2008-02-28
Stopping gdm won't work in this case because X was started manually with startx and gdm is (presumably) not running.

---

### Post by astrotech226 on 2008-02-28
> **sumguy231 said:**
> Stopping gdm won't work in this case because X was started manually with startx and gdm is (presumably) not running.

No...  Those were the steps I took on my PC to test it.  I was running gdm and had to stop it to perform the test.  I was just pointing out that it worked for me and what the differences were.

---

