---
title: "Firefox version confusion"
date: 2007-08-09
forum: General Help
---

### Post by Cordate on 2007-08-09
According to Synaptic, I have Firefox 2.0.something installed, but according to some websites, my broswer is reporting itself as version 1.5. 

Is it possible I have 2.0 somewhere and it is not being used, or is my browser somehow reporting the wrong version?

---

### Post by apetresc on 2007-08-09
> **Cordate said:**
> According to Synaptic, I have Firefox 2.0.something installed, but according to some websites, my broswer is reporting itself as version 1.5. 

Is it possible I have 2.0 somewhere and it is not being used, or is my browser somehow reporting the wrong version?

What does "Help->About Mozilla Firefox" claim? That's very likely to be what it's reporting itself as, as well. Unless something very strange is going on.

---

### Post by Cordate on 2007-08-09
It says 1.5, I would have checked that earlier but I had the Help menu configured to be hidden.

---

### Post by apetresc on 2007-08-09
> **Cordate said:**
> It says 1.5, I would have checked that earlier but I had the Help menu configured to be hidden.
Ah, okay. Since you say that Synaptic definitely tells you you have 2.0something installed, then probably you have *both* versions installed, and the menu entry you use points to the old one.

So how do you usually launch Firefox? And what does Help->About say if you launch firefox using "firefox" at the terminal instead?

---

### Post by Cordate on 2007-08-09
Terminal launch gives me the same version. I usually use the gnome Applications -> Internet -> Firefox link. I also have Firefox set up somewhere in my apps to fire up when the computer boots.

Edit: someone helped me find where the -real- 2.0 was living (/usr/lib/firefox/firefox) and I've got it sorted out now. Hopefully the old ones are gone :)

---

