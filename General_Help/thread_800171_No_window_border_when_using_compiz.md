---
title: "No window border when using compiz"
date: 2008-05-19
forum: General Help
---

### Post by - 000 - on 2008-05-19
Whenever I enable effects in Kubuntu, my border dissapears and I don't know how to recover it.  How do I fix this?

---

### Post by Forlong on 2008-05-19
Is Compiz actually running?

You can check by running ```
ps -o comm= -C compiz.real
```

---

### Post by BlackDragonBE on 2008-05-19
Your system probably can't run Compiz, I had the same on my old laptop, all my borders would just dissappear.

---

### Post by - 000 - on 2008-05-19
> **Forlong said:**
> Is Compiz actually running?

You can check by running ```
ps -o comm= -C compiz.real
```
It doesn't say anything when I do it

---

### Post by Forlong on 2008-05-19
Post the output of [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by - 000 - on 2008-05-19
Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected.

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you won't be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards.

---

### Post by Forlong on 2008-05-19
I was talking about the output before that.
Distribution etc.

---

### Post by - 000 - on 2008-05-19
My bad

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

---

### Post by Forlong on 2008-05-19
Are you sure there are really no boarders at all?
Because there's someone [here]("http://forum.compiz-fusion.org/showthread.php?t=8390") with a similar issue.

---

