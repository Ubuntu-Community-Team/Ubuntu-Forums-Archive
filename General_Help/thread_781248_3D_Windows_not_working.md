---
title: "3D Windows not working"
date: 2008-05-04
forum: General Help
---

### Post by Tryfon on 2008-05-04
Hi all!
My 3D windows effect stopped working ever since I updated in Hardy. I even tried to reinstall the whole compiz stuff but nothing changed. 
When I check the 3d windows option in Advanced Desktop Effects Settings it unchecks by itself a few seconds later! What's going on? I really liked that effect!Everything else seems to be working just fine.
Any clue?

---

### Post by ubockto on 2008-05-04
Perhaps your graphics card isnt as powerful as you would think it to be

---

### Post by Tryfon on 2008-05-04
That was an incredibly scientific approach!
Had you read a bit more carefully what I previously wrote, you would realize that the effect **used** to work until I updated my system. And it worked smoothly.
Nevertheless my laptop bears a nvidia GeForce Go 7600 (with proprietary drivers loaded) and I don't think that it isn't powerful enough.

PS: Smartass approaches don't seem to match the philosophy behind this forum.

---

### Post by ubockto on 2008-05-04
Sorry, that gfx, is good enough to do it, though I do have the Desktop equivalent of your laptop version. Have you tried to install the drivers from nvidia?

---

### Post by chrisruls00 on 2008-05-04
This happened to me. Installing the plugin from Git seems to fix it. Try this:

Make a folder called compiz in your home folder. Start a terminal. then do:

```

cd compiz
git clone git://anongit.compiz-fusion.org/fusion/plugins/3d
cd 3d
make
sudo make install

```

Then restart Compiz and try to turn 3d on again.

---

### Post by Martje_001 on 2008-05-04
If that doesn't work, try to install whole compiz from git. See my signature.

---

### Post by Tryfon on 2008-05-04
chrisruls00 I tried to follow your instructions and when I entered the make command I got the message:
Makefile:48: *** [ERROR] Compiz not installed.  Stop.

Of course that is not right because I have compiz installed through the Synaptics manager and several effects operating. Any idea?

---

### Post by Martje_001 on 2008-05-04
> **Tryfon said:**
> chrisruls00 I tried to follow your instructions and when I entered the make command I got the message:
Makefile:48: *** [ERROR] Compiz not installed.  Stop.

Of course that is not right because I have compiz installed through the Synaptics manager and several effects operating. Any idea?
The version form git (which you try to install) does not match the version which is installed, so the makefile reports an error.

Please try my signature

---

### Post by Tryfon on 2008-05-05
I followed Inxsible's [guide]("http://ubuntuforums.org/showthread.php?t=533201") and completely removed compiz and then reinstalled it through the Synaptics package manager and everything works just fine now! Thank you all for your help!

---

### Post by ubockto on 2008-05-05
good to know everything is now working

---

