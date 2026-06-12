---
title: "k3b not loading"
date: 2007-06-12
forum: General Help
---

### Post by use a name on 2007-06-12
On my Edgy install, k3b works, on Feisty, it does not. In the mean time, it seems to be always running, as it is always in the process list, but the process cannot be killed. Running it from the command line does not give any feedback.

I've tried the 'remove completely' option in synaptic, I've deleted the contents of ~/.kde/share/apps/k3b, didn't help. Any ideas?

---

### Post by LollYouSuckZor on 2007-06-12
```

sudo apt-get remove k3b
```?

and K3b will work on fiesty, it just runs massive amounts of megs.

---

### Post by use a name on 2007-06-12
Removal works, but the problem persists (after reinstallation of course).

I'm going to try something else, inspired by your post. I'll remove k3b, reboot to get rid of the process that is always there and then reinstall it.

---

### Post by LollYouSuckZor on 2007-06-12
=D Good Luck!

---

### Post by use a name on 2007-06-12
Nope, no luck... The ghost process was gone, but after 'starting' k3b it is there again. Two 'instances' were launched, only one was killable.

---

### Post by LollYouSuckZor on 2007-06-12
Weird.. =[, Any ideas?

---

### Post by use a name on 2007-06-25
Bump... :)

---

