---
title: "Root console and gedit freezing. Help please...."
date: 2008-06-06
forum: General Help
---

### Post by spaise on 2008-06-06
Ok Firstly Forgive me if this is posted in the wrong thread.

I seem to be having problems with root console, and gedit.

everytime i try to open root console or gedit, the window opens then freezes and dims out, then asks me to force quit it.

This is rather annoying seeing as i cant really edit stuff without my root console and gedit.

If anyone can shine a light on this it would be much appreciated.

Spaise

---

### Post by aysiu on 2008-06-06
Can you paste this command into the normal (not root) console and post back any error messages you get? ```
gksudo gedit
```

---

### Post by spaise on 2008-06-06
right i inserted that cmd into console... and it done nothing which means its working correctly yes?

---

### Post by aysiu on 2008-06-06
Can you be more specific than "does nothing"? Does the next prompt line appear? Does the command just hang?

---

### Post by spaise on 2008-06-06
sorry my bad, the next prompt line appears

---

### Post by spaise on 2008-06-06
bump

---

### Post by aysiu on 2008-06-06
So in other words ```
spaise@ubuntu:~$ gksudo gedit
spaise@ubuntu:~$
``` is what you see?

Maybe this might help:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by spaise on 2008-06-06
Yep, thats exactually what i see

---

### Post by aysiu on 2008-06-06
> **spaise said:**
> Yep, thats exactually what i see
So try the link I posted.

---

### Post by spaise on 2008-06-06
didnt help much, i can already use sudo from the console, just not root console and gedit

---

### Post by briandu on 2008-06-06
may I suggest you ensure ur pc is at the latest spec. if u use initial release then there are probs.

open xterm and enter:
sudo apt-get update

I assume u r using HH?

then enter:
sudo reboot

and check it again

---

### Post by spaise on 2008-06-06
bump

still didnt help

---

### Post by spaise on 2008-06-07
seems no one knows what to do then?

---

### Post by spaise on 2008-06-07
bump...again lol

---

### Post by Azegul on 2008-06-08
I have the same problem. I can't use gedit to open system files. 
It all came about after this:  Error starting the GNOME Settings Daemon [http://ubuntuforums.org/showthread.php?t=587410&page=5](http://ubuntuforums.org/showthread.php?t=587410&page=5)

I'm still searching the net for answers and will keep looking. I'm not sure if it's related to my Gnome settings problem.

---

