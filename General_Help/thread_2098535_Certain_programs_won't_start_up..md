---
title: "Certain programs won't start up."
date: 2012-12-26
forum: General Help
---

### Post by limelight22 on 2012-12-26
It's mostly games; Red Eclipse, Battle for Wesnoth, Assault Cube, etc. Anyone know what's going on?

---

### Post by limelight22 on 2012-12-26
Anyone? I'm at a loss here.

---

### Post by fantab on 2012-12-26
Welcome to the forum!

When requesting for help PLEASE give us as much information about your Desktop/Laptop and about Ubuntu version you are using. Tell us also how you've installed these games. Otherwise it is difficult to offer any substantial help.

Try running these games from the Terminal and post what output you get. For instance run:

```
$ red eclipse
```

---

### Post by limelight22 on 2012-12-26
loading enet..
loading game..
loading sdl..
loading video mode..
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13


This is what it says when I try to run Red Eclipse from the terminal. I've installed it from the Ubuntu Software Center. I'm on a Compaq Presario CQ60, running Ubuntu 12.10.

---

### Post by kaldor on 2012-12-26
> **limelight22 said:**
> Anyone? I'm at a loss here.

We need some information about your graphics. Can you tell us what brand (Intel, AMD/ATI, NVIDIA) or model (eg. Intel HD 4000) you're using? 

There's a chance you may need to install proprietary drivers for your video card.

Edit: We posted at the same time :)

I found that your graphics device is "*Intel Graphics Media Accelerator 4500M*" according to the HP/Compaq product page. You do not need to install any additional drivers for this card. It should work- I'll see if there's anything weird related to the older Intel cards.

Edit 2: I found this post with a similar issue: [http://ubuntuforums.org/showpost.php?p=12130291&postcount=3](http://ubuntuforums.org/showpost.php?p=12130291&postcount=3) 
thread: [http://ubuntuforums.org/showthread.php?t=2032998](http://ubuntuforums.org/showthread.php?t=2032998) (first post is also relevant)

Do not run the second command if you aren't familiar with it; this assumes you know what you're doing. If you need help with the first one, reply :)

---

### Post by limelight22 on 2012-12-27
Can you explain what all of this means to me? Also I don't think it has to do with my video card, games have worked on this machine before, including the ones that won't work now.

---

