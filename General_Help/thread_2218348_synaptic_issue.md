---
title: "synaptic issue"
date: 2014-04-20
forum: General Help
---

### Post by windowsfree on 2014-04-20
having this issue installing software.  using 14.04 xubuntu


Thank you

---

### Post by sammiev on 2014-04-20
From the terminal window:

```
sudo apt-get install synaptic
```

---

### Post by windowsfree on 2014-04-20
it installed, but will not launch.

---

### Post by rbmorse on 2014-04-20
sudo synaptic

---

### Post by ibjsb4 on 2014-04-20
This has happen to me in the pass and I found that going to /usr/share/applications/synaptic and change Exec=synaptic-pkexec to Exec=gksudo synaptic has worked for me.

---

### Post by bapoumba on 2014-04-20
May be this ? [http://ubuntuforums.org/showthread.php?t=2210892](http://ubuntuforums.org/showthread.php?t=2210892)

---

### Post by zika on 2014-04-20
> **rbmorse said:**
> *_**sudo**_* synapticUsing GUI application with _***sudo***_ is prone to very nasty errors lurking in the dark...
Use **gksu(do)** or **sudo -H**... It is simply surreal that after all talks we've had here about that still we have to see sudo used for GUI application... ;)

---

### Post by windowsfree on 2014-04-21
Hello,

I appreciate all the responses,  I believe we are doing "workarounds" instead of solving the issue.  For me the workarounds are fine, but if Ubuntu has put it in the code, it should be working.

Thank you everyone who has responded.  I will attempt to run synaptic manager by terminal.

Sincerely,

---

