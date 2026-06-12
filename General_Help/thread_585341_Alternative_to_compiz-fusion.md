---
title: "Alternative to compiz-fusion"
date: 2007-10-21
forum: General Help
---

### Post by enchance on 2007-10-21
I can't get compiz-fusion to work in my laptop. What other eyecandy would you suggest and how do I install them (and uninstall compiz)? Thanks.

---

### Post by sci-fi guy on 2007-10-21
Did you install from safe-graphics mode on the LiveCD? That is the only reason for it not working I can think of. Did you use Beryl and/or Compiz under Fiesty? Do you have a decent video card?

---

### Post by enchance on 2007-10-21
No, I didn't install from Safe Graphics mode since I didn't know it had to be done that way. And Yes, my videocard can handle compiz-fusion since I ran "$ glxinfo | grep direct" and it came out as "Yes" meaning my laptop can handle it.

What's the difference if I installed from Safe Graphics mode, will it really help putting compiz-fusion up? I'm using Gutsy.

---

### Post by RAOF on 2007-10-21
> **enchance said:**
> No, I didn't install from Safe Graphics mode since I didn't know it had to be done that way. And Yes, my videocard can handle compiz-fusion since I ran "$ glxinfo | grep direct" and it came out as "Yes" meaning my laptop can handle it.
...

That tells you that your graphics drivers provide 3D rendering to clients, bypassing the X server.  It doesn't tell you that your card/driver is capable of running Compiz - working 3D is only one of the requirements of Compiz.

If you could attach the ~/.xsession-errors file from your home directory, we could check out why Compiz isn't starting - it checks for and logs a bunch of stuff on startup, and writes that log to this file.

---

### Post by enchance on 2007-10-22
I've never opened~/xsession-errors file before. I don't know what part to post so I'll just post everything if it's ok with you.  [View the text file here.]("http://www.joimbong.com/x.txt")

---

### Post by enchance on 2007-10-22
What are the benefits of installing in safe-graphics mode?

---

### Post by enchance on 2007-10-22
Anyone? Helllooooo... *scratches head*

---

### Post by RAOF on 2007-10-23
Hm, looking at that xsession-errors file it appears that Compiz itself is working, but that the configuration editor is broken.

This is most likely caused by using (or having used) 3rd party Compiz packages.  You should check your /etc/apt/sources.list file for any 3rd party repositories (most likely the tuxfamily repos), remove them, then run
```

sudo aptitude update
sudo aptitude purge ~ncompiz ~nlibdecoration
sudo aptitude install ubuntu-desktop compiz compiz-gnome compizconfig-settings-manager

```
to update your package lists, remove the 3rd party compiz packages, and then reinstall them.

---

### Post by enchance on 2007-10-24
Wow, how'd you find that out? Yes, I have the tuxfamily repos. Do I just delete them or do I have to replace them with something else?

EDIT: I have a feeling I went to the wrong tutorials when installing Compiz-Fusion. If you'll direct me to the one you used I'd be better off using it. I'm planning on reinstalling Gutsy anyway.

---

### Post by RAOF on 2007-10-25
Here is a quick tutorial on installing Compiz Fusion on Gutsy:
1) Install Gutsy
2) Done.

Gutsy **comes** with compiz fusion installed & enabled by default.  The only thing you might want to do is to install the compizconfig-settings-manager package (from the Ubuntu repositories!) :).

Addendum: I knew (or rather, guessed) you had the tuxfamily repositories enabled because having 3rd party repositories enabled is the number 1 largest cause of Compiz (and often Ubuntu) breakage.

---

### Post by enchance on 2007-10-25
Hehehe...I had an idea you were going to say something like that. I just finished my reinstall and have to update anything including my ATI driver. Right now I'm trying to look for an alternative to using fglrx because of its high use of memory.

---

