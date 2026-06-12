---
title: "[SOLVED] Ubuntu Desktop Changed Into XFCE (Where's Gnome Gone)"
date: 2007-11-16
forum: General Help
---

### Post by Bumblebum on 2007-11-16
Started my system and it's just gone into this new screen, there is a blue background, icons have changed (most of the zips are now blue boxes. My right click menu has my Ubuntu menus in to start programs. It's changed by itself into a desktop called XFCE without me telling it to.

Last time I came on it did some updates, I never changed anything in ubuntu. I only used firefox the last time around. All the programs still work but it's like it's a new desktop.

If anyone know how to get it back to my normal Ubuntu Gnome desktop please tell me.

---

### Post by por100pre1 on 2007-11-16
So I'm not alone!!! Go to the login screen and select Gnome session, login and set Gnome as default. I don't know what is causing this yet, I'm currently looking for a solution. :-k

---

### Post by Bolorino on 2007-11-16
Is "ubuntu-desktop" listed as installed in synaptic?

---

### Post by Bumblebum on 2007-11-16
It's OK, I solved it. Thanks very much for your replys

Here's what I did

Firstly I right clicked and went to System (or settings) Login Windows and selected default session as gnome

rebooted and it didn't work

So I logged out and chose options at the bottom and selected change session and tried gnome - it didn't work

So I logged out again and chose Gnome failsafe - it worked

So I logged out again and chose Gnome, it asked me if I wanted to make this default every time - I selected yes and gnome went in fine

rebooted and now I'm back in gnome properly

Hope you can solve your problem por100pre1 with that

---

### Post by por100pre1 on 2007-11-16
> **Bumblebum said:**
> Hope you can solve your problem por100pre1 with that

Actually we used the same workaround: to change the default session to Gnome instead of XClient Script. The problem here is that in both cases Xclient script is now pointing to XFCE instead of GNOME. This seems to be a bug triggered by some update. :-k

---

### Post by adam_benson on 2008-01-22
Hi there,

I got my updates last night and find I'm looking at the same XFCE environment. I followed the steps of switching to GNOME failsafe and am still looking at XFCE.Will you please advise me as to how to get back to GNOME?

thanks in advance,
Adam

---

