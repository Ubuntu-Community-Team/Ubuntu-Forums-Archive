---
title: "Screen turns black when idle"
date: 2006-10-10
forum: General Help
---

### Post by Flavian on 2006-10-10
Hi guys. This is kind of a dumb question to ask. But I really don't know what's causing the problem. I already checked the system settings a bunch of times and in power management (I have a laptop) I set EVERYTHING to "never", I also checked the screensaver settings and every other option and searched for an entry I might have missed.

The thing is, like I wrote in the title, that for example if I watch a movie after like 15 minutes the screen turns black.
That is annoying, cause I need to get up every 15 minutes and move my mouse...

To ask this question is kind of embaressing to ask, because it sounds like I am a complete idiot :D, maybe I am and I have missed something, but I kinda don't have a clue what's causing the problem...

Would be glad for any help.
Flo

---

### Post by mssever on 2006-10-10
Try typing ```
ps -ef | grep screen
``` at a terminal. Check to see if there's anything that looks like a screensaver that's running. If you see a screensaver (gnome-screensaver for me), kill it: ```
killall gnome-screensaver #or whatever your screensaver is called
```

If it comes back after logging out and back in, then something's weird with your setup. But you can always manually kill it, or write a script to kill it automatically. Of course, the best solution would be to determine why it was still being started.

---

### Post by NeoLithium on 2006-10-10
There also may be power management set up in bios for your laptop (mine does) that always kicks in, no matter what I set my power management to with Ubuntu.  I just set it for like 6 hours after, and doesn't bug me...

---

### Post by Flavian on 2006-10-11
Hi guys:
This is what I get:

```
florian@octavius:~$ ps -ef | grep screen
florian   4737  4689 12 11:37 ?       00:03:08 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer
florian   4908     1  0 11:38 ?        00:00:01 gnome-screensaver
florian   5300  5282  0 12:02 pts/0    00:00:00 grep screen
florian@octavius:~$ killall gnome-screensaver

```

After killing the screensaver I does not change, the screen turns black again :(

---

### Post by jm2003uk on 2006-10-11
> **NeoLithium said:**
> There also may be power management set up in bios for your laptop (mine does) that always kicks in, no matter what I set my power management to with Ubuntu.  I just set it for like 6 hours after, and doesn't bug me...

Yeah, check the BIOS settings. Like NeoLithium said there's usually a power management area of the bios which can control when the screen goes to standby and (on my laptop) fan settings, screen brightness and HD turn off delays.


Hope you get it sorted!

James

---

### Post by mssever on 2006-10-11
The other thing would be to check that gnome-screensaver is indeed dead after killing it.

---

### Post by .t. on 2006-10-11
You may have DPMS options set in xorg.conf. Check it out.

---

### Post by Jolly Roger on 2006-10-11
I have this problem also. ](*,) I believe it is related to having XGL setup. I never previously had this problem before I setup XGL but now I have the exact same symptoms as Flavian. If anyone knows a solution it would be much appreciated.

---

### Post by Flavian on 2006-10-11
Okay here we go... I maybe found a solution buddy :)
This might help you: 
Try adding the following in /etc/X11/xorg.conf

```

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

```

---

