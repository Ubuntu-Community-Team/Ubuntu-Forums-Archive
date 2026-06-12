---
title: "Fluxbox running very slowly"
date: 2005-05-06
forum: General Help
---

### Post by curly08 on 2005-05-06
For some reason, Fluxbox is running very slowly with Ubuntu. It takes forever to start up; a lot of gui-front-end programs take absolutely forever (openoffice, evolution, etc take 5+ minutes to load). Some gui programs don't load at all. Any ideas?

Any help would be apreciated. Thanks.

---

### Post by 23meg on 2005-05-06
reminds me of my attempt at fluxbox with the old Warty. are you using a laptop? is powernowd running?

---

### Post by curly08 on 2005-05-06
It is a laptop and powernowd is running...is this something I need to change?

---

### Post by 23meg on 2005-05-06
maybe; try terminating powernowd, and disabling it altogether so that it doesn't run on boot and see if either one helps.

---

### Post by curly08 on 2005-05-07
How do I disable it completely?

---

### Post by h2gofast on 2005-05-09
I just installed Hoary on an old pII 366 panasonic toughbook and got fluxbox installed.  I was running debian sid.  The only difference is that fluxbox takes longer than gnome to start, but once started it's as snappy as it was under debian.  So it is possible to get flux running satisfactorily.  Now if I could just get it back from suspend.

---

### Post by 014&lt; on 2005-05-10
This should solve the problem. Fluxbox won't be as fast as it is in other distros, but it will be faster than it is now.

[http://www.ubuntuforums.org/showthread.php?t=21328&highlight=fluxbox](http://www.ubuntuforums.org/showthread.php?t=21328&highlight=fluxbox)

---

### Post by bcrowell on 2005-05-11
I'm experiencing the same problem with fluxbox. I've seen the info at [http://www.ubuntuforums.org/showthread.php?t=21328&highlight=fluxbox](http://www.ubuntuforums.org/showthread.php?t=21328&highlight=fluxbox), but am not having any luck applying it to my situation. I'm used to having a .xsession file that starts my fluxbox session, but in this ubuntu install, I have gdm (which I've never used before) rather than xdm, and there's no .xsession file, so I'm having trouble figuring out where to put the "export LC_ALL=C". AFAICT from reading the gdm docs, the equivalent would be a script in /etc/X11/gdm/Sessions. Well, in that directory I have the script /etc/X11/gdm/Sessions/fluxbox, which looks like a script that's actually intended to start fluxbox. However, changing this file has no effect, and I don't think it's even being run. For instance, if I comment out the final line that is actually supposed to start fluxbox, it makes no difference, and fluxbox still starts up. Likewise if I put an  'echo "hello" >~/a.a' in it, it doesn't actually do that when I log in. So is there some script somewhere else that is really what I need to be modifying?

TIA!

---

