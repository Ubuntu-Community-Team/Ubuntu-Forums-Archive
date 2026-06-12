---
title: "Need script to run before X server at boot"
date: 2007-03-22
forum: General Help
---

### Post by MalcolmCarmen on 2007-03-22
[COLOR="Red"]***Resolved!***[/COLOR]

Hello, I have a dell inspiron B130 (Edgy) with an intel video chipset that requires the use of 915resolution ( [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) ), which is a sort of video BIOS hack to replace a given resolution with my desired one. It must always run at boot.

In order to work properly, it must be invoked before X server (this is in the instructions). I thought putting a script in /etc/init.d, +x'ing it, and "update-rc.d fixmyvideoscript defaults" would work, but I suppose the script isn't running before X server, because it isn't working.

Where should I put a script or just my single 915resolution binary invocation if I wish for it to run before X server?

As a side note, I know that 915resolution works, because I can manually use it as root, then alt+control+backspace, and it will be using the proper resolution when it gets back to the gnome login.

Thanks!

---

### Post by Muzik83 on 2007-03-23
Hey,

I'm a little confused as to what you mean when you say "but I suppose the script isn't running before X server, because it isn't working".  I assume you mean 'you tried this, but it probably loaded it after x started, because it didnt work'.

I think you have done right with the update-rc.d, but check and make sure it does in fact run before the X startup.

If you go into /etc/rc2.d/ and have a look, ensure your 'fixmyvideoscript' is something like S10fixmyvideoscript, where 10 is some number before S13gdm (gdm is set to start 13th in my sequence of events, it may be different on your system!).  Make sure its S10 and not K10 (as in kill 10th last)

Make sure everything you need to run your 'myvideoscript' has been loaded before you do it (so a silly example is, if it is on a network share, you have S09samba or S09nfs first to mount the drive)

I hope this helps
-sean

---

### Post by MalcolmCarmen on 2007-03-23
Thanks -- I renamed my "S20fixvideo" script so that it had a number lower than "S13gdm", but that didn't quite seem to work. I decided to figure out how this runlevel madness worked, and then came across a blog article that reminded me of Edgy's use of upstart ( [http://blog.mypapit.net/2007/03/where-can-i-find-inittab-in-ubuntu-edgy-eft-or-feisty-fawn.html](http://blog.mypapit.net/2007/03/where-can-i-find-inittab-in-ubuntu-edgy-eft-or-feisty-fawn.html) )

For anyone else that might happen along here from google, here is the configuration I put in /etc/event.d in a file called "fixvideo":

```

start on startup

start on runlevel 2
start on runlevel 3

start on stopped rcS

start on started tty1


# fix video bios
exec /usr/sbin/915resolution 38 1280 800 24

```

I appreciate the help, I wouldn't have known where to begin looking otherwise :D

---

