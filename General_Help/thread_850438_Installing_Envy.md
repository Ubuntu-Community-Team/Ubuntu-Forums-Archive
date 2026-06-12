---
title: "Installing Envy"
date: 2008-07-05
forum: General Help
---

### Post by ben-ess on 2008-07-05
WEll, I am trying to install envy to fix my screen problem, and when I go into terminal i type

sudo apt-get install envyng-qt

and i get the message 

E: Couldn't find package envyng-qt

I don't know what I'm doing wrong?

---

### Post by drs305 on 2008-07-05
I think envy-qt is probably for kubuntu. Your post designates 'ubuntu'.

```
sudo aptitude install envyng-gtk
```

Try this one. The envyng-qt is listed in synaptic but lists some kde dependencies.

---

