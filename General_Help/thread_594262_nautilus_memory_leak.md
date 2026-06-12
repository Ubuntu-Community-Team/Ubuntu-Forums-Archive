---
title: "nautilus memory leak?"
date: 2007-10-27
forum: General Help
---

### Post by rbhkamal on 2007-10-27
it seems that the process nautilus is growing awfully big on my laptop. It sometimes gets all the way up to 400+MB. Is this normal? is there some type of caching done by this process?
Once I kill it, it restarts and goes back to 20MB when I open one of my sshfs folders it bumps to 32MB and so on and so on....
Any help on fixing this is appreciated.


Regards,
RK

---

### Post by FarJumper on 2007-11-06
I have the same. 
Simplest way to check this is to refresh the desktop several times (F5). Nautilus grows up about 500k each refresh action (i have ~100 icons on my desktop).

---

### Post by Chibi-Tatsu on 2008-02-16
It appears more that it just never decreases; that is, each new directory you open adds some to the memory usage (relating to the number of icons, it seems), and that memory is allocated more or less forever.

Thus for me, when I'm sorting large numbers of pictures in comic book archives (such a convenient way to store pictures), opening up dozens of archives to resize pictures appropriately, it can grow up 800 megs quite quickly.

---

### Post by Meta8 on 2008-02-16
Maybe the bug should be reported?

---

### Post by rbhkamal on 2008-02-20
Could someone please open a bug for this and post the link here. I'm not familiar with Ubuntu bugs tracking system.

---

