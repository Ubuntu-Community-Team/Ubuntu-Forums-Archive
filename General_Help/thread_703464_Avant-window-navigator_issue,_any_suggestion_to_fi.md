---
title: "Avant-window-navigator issue, any suggestion to fix it?"
date: 2008-02-21
forum: General Help
---

### Post by gohanssjn on 2008-02-21
Ok, here are my symptoms.  And to preface it, I have uninstalled and reinstalled many times in an attempt to fix it:

When I add a show desktop Applet or Trash Applet, unpon restarting the computer, they do not show, only white lines
Once AWN loads, I cannot open 'Properties' to change it until a reinstall
When it is set to open upon login, until uninstalled, I can't edit the Main Main in Ubuntu

Any ideas to what the problem is here?

I am running Gusty (7.10), all updates installed, Q6600 on a Gigabyte DSR3, with a BFG 8800GTX.

I do have Compiz running because I use Expo a lot.

I've been thinking maybe it's an nvidia issue...but probably not..

---

### Post by gohanssjn on 2008-02-21
oh, and when i do "Mark for complete removal" and everything in the Package Manager, my settings are still there when I reinstall.  Am I missing the offending file when I uninstall?

---

### Post by MCrittenden on 2008-02-21
I'm afraid I can't help with the AWN applet issue, except to say that I had that problem when I used it a couple months ago, and I have an ATi, so it may not be your video card.

About the settings staying in place, there are a few possible reasons. The most obvious one is that it's leaving a folder in your home directory. It'd probably be named .awn or .avant or something like that (make sure you select show hidden files to find it). I apologize if you've already checked that...just had to make sure. 

The second option is that the residual config is still hiding in there. After you uninstall AWN, go to synaptic, click "status" at the bottom left, select "Not installed (residual config)" and check to see if avant's config file pops up. If so, mark for uninstall. 

Other than that, afraid I can't help. Good luck.

---

### Post by gohanssjn on 2008-02-21
I will try that, thanks!

---

### Post by gohanssjn on 2008-02-21
Well, i think i found the culprit, and it's not pretty.

I restored to a fresh install, and installed AWN, then just started installing other stuff till it broke.

It died when I installed the OSS-XFi drivers.  The one thing I HAVE TO HAVE on this computer.  So depressing :(

---

### Post by Rome.konig on 2008-02-21
what type of video card do you have. i had that problem with my ati video card, you might have to check and make sure the Xorg drivers are working correctly. Do you have Awn in sessions menu? i get best results with Awn when i have it starting when my ubuntu boots.

---

### Post by gohanssjn on 2008-02-21
nVidia card.

And I do have it coming on at boot.  But I cannot change its type for some reason; it always reverts to Setting.  Weird.

Here is a pic of what I get:

---

### Post by gohanssjn on 2008-02-21
Maybe I just wasn't meant to have Ubuntu on my desktop.  It just seems to work on my laptop, but the desktop is just a big hassle.  I can't get my Hauppauge 1600 TV Tuner to work either :(

---

### Post by harold4 on 2008-02-21
What repo are you installing awn from?

---

### Post by gohanssjn on 2008-02-21
> **harold4 said:**
> What repo are you installing awn from?

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

---

### Post by harold4 on 2008-02-21
Try [reacocard's]("http://ubuntuforums.org/showthread.php?t=385981") repo.  It's more current than the tuxfamily repo.

---

### Post by gohanssjn on 2008-02-21
I will try that as soon as I get home :D

---

### Post by MCrittenden on 2008-02-21
[http://ubuntuforums.org/showthread.php?t=607158](http://ubuntuforums.org/showthread.php?t=607158)

Especially look at post # 10, If that doesn't work, try post # 6.

---

### Post by gohanssjn on 2008-02-26
Still no luck.  White lines after I install the OSS sound drivers :(

Where can I get this file to see if it helps?  python-libawn0   I can't apt-get it....

---

### Post by MCrittenden on 2008-02-27
Try these:

i386: [http://getdeb.net/archive/py/python-libawn0_0.2.1-1~getdeb1_i386.deb](http://getdeb.net/archive/py/python-libawn0_0.2.1-1~getdeb1_i386.deb)
AMD64: [http://getdeb.net/archive/py/python-libawn0_0.2.1-1~getdeb1_amd64.deb](http://getdeb.net/archive/py/python-libawn0_0.2.1-1~getdeb1_amd64.deb)

---

