---
title: "AMSN and other program interfaces look weird.."
date: 2007-02-20
forum: General Help
---

### Post by Naatan on 2007-02-20
Ok so I have Ubuntu as my workstation at work, and it all works well, now at home it all works well aswell except that some applications, AMSN being the main one to my concern, have a really ugly interface, the font isn't smoothened at all and the mouse is different and horizontally converted, all together it feels like im working in an OS that's extremely out of date, as far as the looks go, note that this only goes for AMSN and some other apps though, the rest of ubuntu looks fine.

I've attatched a screenshot to show you what it looks like.

Now at my work I use AMSN aswell and it looks fine there.. I've done a clean install of ubuntu and I haven't really changed all that much about it.

Also I've tried installing it from the package on the amsn website, threw Automatix and threw synaptec package manager.. none of which gave any visual difference.

So.. hope someone here can help :)

---

### Post by r4ik on 2007-02-20
Try,

[http://www.ubuntuforums.org/showthread.php?t=297676&highlight=AMSN](http://www.ubuntuforums.org/showthread.php?t=297676&highlight=AMSN)

---

### Post by Naatan on 2007-02-20
hmm I get the following error when installing that script ->

```
Setting up gtk-engines-eazel (0.3-5.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing gtk-engines-eazel (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 gtk-engines-eazel
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any idea what dependencies I should install to make the anti-aliasing work? I can simply do it manually instead

---

### Post by Naatan on 2007-02-20
nvm.. I removed the eazel engine and it works! :D thanks! :)

---

### Post by r4ik on 2007-02-20
You're welcome.

---

### Post by shironeko on 2007-02-20
XMMS has the same problem.

---

### Post by pickarooney on 2007-05-19
> **shironeko said:**
> XMMS has the same problem.

The best 'fix' for that is probably to install audacity (or beep media player)

---

