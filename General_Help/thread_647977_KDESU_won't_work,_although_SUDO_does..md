---
title: "KDESU won't work, although SUDO does."
date: 2007-12-23
forum: General Help
---

### Post by jlacroix on 2007-12-23
I have a really weird problem.

I noticed that if I click on Adept or Synaptic in my Kmenu, they won't load at all. If I have an update to install, and the Adept Updater icon is showing by my clock, nothing happens when I click on it.

If I go to a terminal and type "sudo synaptic" or "sudo adept_manager" those apps will work fine.

If I type "kdesu synaptic" or "kdesu adept_manager" I get the following error:

> Xlib: connection to ":0.0" refused by server
Xlib:
No protocol specified

This is really weird, it was working about a week ago, I didn't make any configuration changes to my machine.

Does anyone know what could be wrong?

---

### Post by PeterJS on 2007-12-23
> **jlacroix said:**
> I have a really weird problem.

I noticed that if I click on Adept or Synaptic in my Kmenu, they won't load at all. If I have an update to install, and the Adept Updater icon is showing by my clock, nothing happens when I click on it.

If I go to a terminal and type "sudo synaptic" or "sudo adept_manager" those apps will work fine.

If I type "kdesu synaptic" or "kdesu adept_manager" I get the following error:



This is really weird, it was working about a week ago, I didn't make any configuration changes to my machine.

Does anyone know what could be wrong?

I did this to my self a while ago. Some how, I haven't gone to the effort to replicate it so I can't tell you the initial cause, your  Xauthority file got changed to root ownership, I'm not sure what all it does, but it contains the "Magic Cookie" (I'm not making the name up, when you're done go take a look), that tells X it's allowed to accept connections from a program.

To fix your problem:
```

sudo rm ~/.Xauthority

```
And then ctrl+atl+backspace to restart X and you should be good to go.

---

### Post by ~LoKe on 2007-12-23
Using sudo for gui's instead of gksudo could cause this problem.

---

### Post by PeterJS on 2007-12-23
> **~LoKe said:**
> Using sudo for gui's instead of gksudo could cause this problem.

Good to know, I'm notoriously bad about doing that. I didn't know that XFCE had a run dialog for a long time and would just pop open terminals and run graphical commands with sudo.

---

### Post by jlacroix on 2007-12-24
> **PeterJS said:**
> I did this to my self a while ago. Some how, I haven't gone to the effort to replicate it so I can't tell you the initial cause, your  Xauthority file got changed to root ownership, I'm not sure what all it does, but it contains the "Magic Cookie" (I'm not making the name up, when you're done go take a look), that tells X it's allowed to accept connections from a program.

To fix your problem:
```

sudo rm ~/.Xauthority

```
And then ctrl+atl+backspace to restart X and you should be good to go.

I did as you asked, and I am still having the same problem.

From the terminal:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified



(synaptic:17061): Gtk-WARNING **: cannot open display:


Upon my further investigation, it looks like gksudo works for everything, kdesu works for nothing. This also means I cannot use Adept updater.

---

### Post by p_quarles on 2007-12-24
> **jlacroix said:**
> Upon my further investigation, it looks like gksudo works for everything, kdesu works for nothing. This also means I cannot use Adept updater.
No, it doesn't mean that. There's nothing wrong with running Qt applications with Gnome graphical sudo application. Certainly preferable to running a graphical app with sudo. 

Generally, you should use the version of graphical sudo that is most appropriate for the DM you're using. Since you're using Xfce, you should use gksudo.

---

### Post by jlacroix on 2007-12-24
> **p_quarles said:**
> No, it doesn't mean that. There's nothing wrong with running Qt applications with Gnome graphical sudo application. Certainly preferable to running a graphical app with sudo. 

Generally, you should use the version of graphical sudo that is most appropriate for the DM you're using. Since you're using Xfce, you should use gksudo.

I'm using KDE. kdesu doesn't work under KDE, which means when the Adept updater icon comes up next to my clock, clicking on it or the Adept Manager icon does nothing.

---

### Post by jlacroix on 2007-12-25
Anyone? Please? :(

---

### Post by PeterJS on 2007-12-25
Have you looked in to the Xautority file's permissions?

---

### Post by zekica on 2007-12-25
If you are using Gutsy, can you try to use **kdesu.distrib** instead of **kdesu**?

If it works, you can then do:
**sudo mv /usr/bin/kdesu /usr/bin/kdesu.kubuntu**
**sudo ln -s /usr/bin/kdesu.distrib /usr/bin/kdesu**

To replace Ubuntu installed kdesu with the one that comes with KDE.

---

### Post by jlacroix on 2007-12-25
> **zekica said:**
> If you are using Gutsy, can you try to use **kdesu.distrib** instead of **kdesu**?

If it works, you can then do:
**sudo mv /usr/bin/kdesu /usr/bin/kdesu.kubuntu**
**sudo ln -s /usr/bin/kdesu.distrib /usr/bin/kdesu**

To replace Ubuntu installed kdesu with the one that comes with KDE.

Yes! Thanks! That did the trick.

---

### Post by dardhal on 2008-04-28
> **jlacroix said:**
> Yes! Thanks! That did the trick.

Same, although the problem was that after upgrading to kubuntu 8.04 from kubuntu 7.10 kdesu stopped working: after the upgrade I was always getting the following error:
> No protocol specified
Error: Can't open display: :0

But the trick did it. Hope this helps, and thank you to the person that suggested the workaround.

---

