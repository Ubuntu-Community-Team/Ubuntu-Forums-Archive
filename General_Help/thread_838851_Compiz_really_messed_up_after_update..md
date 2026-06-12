---
title: "Compiz really messed up after update."
date: 2008-06-23
forum: General Help
---

### Post by clyde9999 on 2008-06-23
I have a Satellite A75-S206 with an ATI Mobility 9000, after this last update (I updated, 23 June, 2008), Compiz is slow, sluggish, lines appear on my desktop. It is awful. Worked great before the update! Hope someone can hlep.

---

### Post by himynameiskevin on 2008-06-23
mine broke entirely using an ati xpress 1150 and aiglx. haven't really looked into it yet

---

### Post by himynameiskevin on 2008-06-23
okay, i just had to load this into /usr/bin/compiz

```
LIBGL_ALWAYS_INDIRECT="true"
SKIP_CHECKS="yes"
```

but that's because i had to edit mine to make it run before, and the update changed the file.

---

### Post by Forlong on 2008-06-24
**[COLOR="Red"]Do not mess with /usr/bin/compiz[/COLOR]**

Use this instead: [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

This will take care of it as well: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by pmlxuser on 2008-06-24
Easiest if you are connected remove it completely from synaptic Package Manager, then reinstall it again. perfect...

---

### Post by Rocket2DMn on 2008-06-25
For the slowness problem, remove xgl if it is installed
```
sudo apt-get remove --purge xserver-xgl
```
Here is a link about using SKIP_CHECKS - you're not supposed to put it in /usr/bin/compiz - see here: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
I think Forlong's script will automatically perform the appropriate SKIP_CHECKS method for you.

---

