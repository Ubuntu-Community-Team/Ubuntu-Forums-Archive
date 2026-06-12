---
title: "[SOLVED] Where is X?"
date: 2007-07-07
forum: General Help
---

### Post by Stebbins on 2007-07-07
I am trying to install Six ([http://six.retes.hu/](http://six.retes.hu/)).  When I run ./configure, I get an error message that says "Can't find X libraries. Please check your installation and add the correct paths!"

Looking at my PATH variable, it looks like it points to the location of the X libraries, but apparently not.  My PATH = usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/X11R6/bin:/usr/X11R6/lib:.

Can anyone tell me where to find X?

---

### Post by dfreer on 2007-07-07
> **Stebbins said:**
> I am trying to install Six ([http://six.retes.hu/](http://six.retes.hu/)).  When I run ./configure, I get an error message that says "Can't find X libraries. Please check your installation and add the correct paths!"

Looking at my PATH variable, it looks like it points to the location of the X libraries, but apparently not.  My PATH = usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/X11R6/bin:/usr/X11R6/lib:.

Can anyone tell me where to find X?

Generally, when compiling, you'll need the developer's libraries alongside of the regular libs. This might be what you are looking for:
```
sudo apt-get install libx11-dev
```
Although I can't be sure.

---

### Post by p_quarles on 2007-07-07
According to the link you posted, there's a Debian package available for that game. Just get that, so you don't have to bother compiling. And messing around with your X libraries, if you don't know where they are, is ilkely not going to work out very well.

---

### Post by Stebbins on 2007-09-24
Thank you both very much.  I've been able to resolve the problem.

---

### Post by dfreer on 2007-09-24
Would you mind posting what the solution was, for others that run into the same problem as you?

---

