---
title: "Ubuntu 16.04 cannot start second X session"
date: 2016-07-12
forum: General Help
---

### Post by piotr-tarnowski-mail on 2016-07-12
Hi guys I'm looking for a little help, I've just upgrade my system to 16.04 version, but I have some problems with my scripts for wine apps which were working on 14.04 version.
To be honest it is not even with my script but with xinit command itself.

Fresh ubuntu instalation + nvidia drivers, beside of mentioned issue everything is working perfectly I can log in into the system, run any 3D app/game but when I try to run simple command "xinit" from terminal I go nothing but black screen :-( 
In default there should be xterm running in seperate tty it is working like that in 14.04... but here "nothing".

There is no errors in /var/log/Xorg.$.log and it is almost the same as in /var/log/Xorg.0.log (the primary x server) everything seems to be initialised perfectly but when I run xrandr -q I got almost nothing only [COLOR=#111111][FONT=Consolas]Screen 0: minimum 320 x 200, current 1368 x 768, maximum 8192 x 8192[/FONT][/COLOR]

On my primary server in 16.04 there are a lot of stuff modelines etc... on 14.04 I have on primary and secondary server the same output.
I don't really know what is going on I even try to load custom xorg.conf with xinit command and configuration has been read (new it from logs)

I will appreciate any help.

---

### Post by DuckHook on 2016-07-13
Welcome to the forums, piotr-tarnowski-mail.

I am not sure that I understand your question. Are you trying to start another xsession on, say TTY6? This is not possible unless you create another account and log into it using that account. You cannot run two separate xsessions under the same login.

If you are trying to run an xsession in *Terminal* (the terminal emulator that runs as a window in your primary xsession), then this is especially impossible even with another login, because *Terminal* is a pseudo-terminal and not a real one.

---

### Post by ubfan1 on 2016-07-20
Hmmmm, I got here even though the Forums are shut down, through the google result.  Anyway, if this answer ever appears anywhere:
Yup, the 16.04 X server no longer allows an easy start by a non-root user.  The "start" does involve an unused vt, like vt8, and used to work on 14.04.
Non-starter "solutions"---
  1)Edit /etc/X11/Xwrapper.config   Nope, the file no longer exists, doesn't do what you want even if you create it.
  2) run dpkg --reconfigure x11-common   Nope, that no longer brings up the window to allow all users, dies doing nothing.
  3) reinstall the x11-common-legacy    This might actually work, if you can accept running with the old X server.
  4) Run as root.  Maybe, but doing this tends to leave root owned files in your login directory which prevents normal logins.

The old command which used to work looked like (from a normal X term):
xinit /usr/games/xsnow -- :1 vt8
And started an X server on screen :1 running xsnow on vt8

---

### Post by Zorgoth on 2016-07-28
Running Ubuntu 16.04 with the xfce4 package installed, I was able to hit ctrl-alt-f2, log in to my the same user account, and run

xinit /usr/bin/xfce4-session -- :1 vt2

There were some annoyances (for example, if I opened chrome on TTY2 and then tried to open one on TTY7, it would open on TTY2 instead). Also, XFCE pops up with a bunch of warnings about conflicts with the Unity session that's already running. However, I am able to turn off xfce's compositing, then open steam and run a game in wine. If I'm in the audio group (and have relogged since adding myself), I can hear sound from both TTYs simultaneously. I can switch back and forth with no issues - the game doesn't crash or anything.

All in all, it did everything I need it to do (there's no reason for me to run chrome in TTY2 anyway -- it's exclusively for playing games, and it's easy to hit Ctrl-Alt-F7 to get back to where I want to be).

---

### Post by Zorgoth on 2016-07-28
You can also use two different user accounts, which results in a different set of weird interactions. You can share a wine prefix as I describe here (the answer from today/this year) to help with this approach: [http://askubuntu.com/questions/558323/how-to-share-wineprefix](http://askubuntu.com/questions/558323/how-to-share-wineprefix)

---

### Post by kloszard on 2016-08-25
It's [bug #1562219]("https://bugs.launchpad.net/ubuntu/+source/xinit/+bug/1562219").

---

### Post by ubfan1 on 2016-11-23
[**[COLOR=#000000]piotr-tarnowski-mail[/COLOR]**]("https://ubuntuforums.org/member.php?u=2037575"), try running with the nouveau driver instead of the Nvidia driver.  Then logging into a virtual terminal, e.g. vt2, and running xinit -- :1 vt2  should start your default xterm on display :1 .

---

### Post by kloszard on 2016-12-28
Please try to run it like this on proprietriary drivers:

```
xinit /usr/bin/dbus-launch --exit-with-session /usr/bin/openbox-session  -- :1 vt<tty_number>

<tty_number> - tty you are running; 1 to 6.
```

It works for me on both Intel HD 3000 open source drivers and on Nvidia proprietary drivers ver. 367.57.

---

