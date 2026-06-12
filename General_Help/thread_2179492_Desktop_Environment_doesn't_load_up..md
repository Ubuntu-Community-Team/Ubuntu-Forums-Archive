---
title: "Desktop Environment doesn't load up."
date: 2013-10-08
forum: General Help
---

### Post by lanser2 on 2013-10-08
I have just installed Xubuntu 4 weeks ago, everything was working exactly fine, but now. when I log in, and enter my password, I can only see my cursor and the Xubuntu background, my wallpaper, panels, icons take like 70-90 seconds to load up. Like, I have to wait a lot. What is this causing this problem? Here is the output of my dmesg: [http://pastebin.com/mkPSa9kw](http://pastebin.com/mkPSa9kw)

---

### Post by Toz on 2013-10-08
Try clearing out your sessions cache (it might either be corrupted or there is something timing out during startup). If you have Xubuntu 13.04 or later, you'll find the "Clear saved sessions" button in Settings Manager->Session and Startup->Sessions tab. 

If you have an earlier version, you'll have to manually clear it before you log in. At the login screen:
- press Ctrl+Alt+F1 to go to the first console.
- log in to the text console
- run the following commands:
```
cd .cache
rm -rf sessions
```
- go back to the gui console by pressing Ctrl+Alt+F7
- try logging in to see if there is a difference.

If you still have problems, **~/.xsession-errors** or **~/.xsession-errors.old** would be the log files that might provide more information.

---

### Post by lanser2 on 2013-10-09
I removed the .sessions directory in .cache but still did not solve my problem, and here are the log files: .xsession.errors file: [http://pastebin.com/kpMH91Rn](http://pastebin.com/kpMH91Rn) &
/var/log/Xorg.0.log file: [http://pastebin.com/Rb7QasGX](http://pastebin.com/Rb7QasGX)

---

### Post by Toz on 2013-10-09
A couple of questions:
1. What version of X/Ubuntu are you using?
2. Is this a straight Xubuntu install or an Xfce on Ubuntu install?

A couple of suggestions:
1. Remove the indicator plugin from the panel and log out and back in again to see if the problem is gone. Post back ~/.xsession-errors again.
2. Try logging in as another user (or guest). Does the problem also happen for this other account?

---

### Post by lanser2 on 2013-10-11
I am using Xubuntu 12.04, and it is a straight Xubuntu install.


I tried logging in as guest, root, and 2 other users to see if this solved the problem, but unfortunately no.
I also removed the indicator-plugin from the panel and rebooted, and it still didn't solve the problem.

here's the .xsession-errors file after the indicator-plugin removal: [http://pastebin.com/6i9CHyP5](http://pastebin.com/6i9CHyP5)

---

### Post by Toz on 2013-10-11
Can you post back a listing of your autostart apps:
```
ls ~/.config/autostart
```
...and the list of running processes:
```
ps -U $USER -u $USER u
```

---

### Post by lanser2 on 2013-10-11
/config/autostart: [http://pastebin.com/2WSJMRYF](http://pastebin.com/2WSJMRYF) 

P.S: I really don't need the bluetooth-applet.

ps -u $USER -u $USER u output: [http://pastebin.com/Qci32HCE](http://pastebin.com/Qci32HCE)

---

### Post by Toz on 2013-10-11
From your dmesg:
> [   57.609050] accounts-daemon[1780]: segfault at 622d6d75 ip b76ee7c3 sp bffe8a40 error 4 in libdbus-1.so.3.5.8[b76c9000+47000]
...You might be suffering from a variant of [this bug]("https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1004515").


> I tried logging in as guest, root, and 2 other users to see if this solved the problem, but unfortunately no.
...Since you've stated that you notice the same slowdown when logging in with guest or other users, its probably something system-wide.


> 
lanser    2584  0.0  0.0   7516  2524 ?        S    14:17   0:08 xscreensaver -no-splash
...
lanser    3115  0.0  0.1  38616  6200 ?        Sl   14:55   0:00 /usr/bin/gnome-screensaver --no-daemon
...
lanser    4903  0.0  0.1  44564  5400 ?        Sl   17:23   0:01 /usr/bin/zeitgeist-daemon
lanser    4912  0.0  0.2  55892  7504 ?        Sl   17:23   0:07 zeitgeist-datahub
lanser    4913  0.0  0.2  52332  8752 ?        Sl   17:23   0:01 /usr/lib/zeitgeist/zeitgeist-fts
When did you notice the slow-down? Did you install something at the same time? I notice that you have gnome-screensaver and zeitgeist installed - neither are part of the vanilla Xubuntu install. Can you post back **/var/log/apt/history.log** and lets try to see what was installed at the time that you noticed the slowdown.

Can you also post back **/var/log/lightdm/lightdm.log**?

FYI: you also have 2 screensavers running, you should probably uninstall one of them.

---

### Post by sogood007 on 2013-10-12
I have similar issue with login (I am using Kubuntu) .   I ended uninstall lightdm and pick gdm during the uninstall.  I can login my kde session again.

---

### Post by lanser2 on 2013-10-13
I fixed this issue by simply installing gir1.2-accountsservice-1.0, although now I have to wait like 5-7 seconds, before this, I had to wait 60-70 seconds, the wait-time has decreased to 5-7 seconds, and when I login, the usage of RAM is 225 RAM, when I first installed Xubuntu, the ram-usage was just 190MB, how can I make my system use just 190MB at startup? Can you please tell me which useless services I can disable so my system uses less memory at startup, (P.S: I don't want bluetooth, tumblerd, or any other useless service running).

---

### Post by Toz on 2013-10-13
You've installed a gnome app or apps that have brought in some extra dependencies (notify-osd, gnome-screensaver, zeitgeist, etc) that are taking up the extra memory. You can try uninstalling them, but because of the dependency chain, it might uninstall the gnome app(s) you installed in the first place. Do you recall which gnome apps you installed? /var/log/apt/history.log might help identify them.

---

