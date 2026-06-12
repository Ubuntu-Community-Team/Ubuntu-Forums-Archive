---
title: "cannot access synaptics in gui! Help!"
date: 2008-05-22
forum: General Help
---

### Post by Vivian-Synecdoche on 2008-05-22
Heylow friends!

I've been Ubuntu for quite some time and I've come to love it. I've dealt with a lot of problems just by reading these forums and have come to love entertaining myself by customizing my desktop.

However, after some installation and removals via apt-get (not aptitude), I have realized to my horror that I cannot access most of my 'secured' (meaning: windows that ask for passwords) windows. Most prominent is synaptic. When I click on it via the menu, it nothing happens - not asking for my password at all. 

However, I seemed to be able to access it via terminal via:
sudo synaptic
After confirming my password in terminal, it opens perfectly.

What's wrong here? Please help me!

---

### Post by N.N. on 2008-05-22
Sounds like you somehow broke gksudo, which is the graphical GTK+ front-end for su and sudo.

In order to diagnose why it won't start, launch it from the terminal and scrutinise the error messages that it outputs. Try starting Synaptic with gksudo, for instance: ```
gksudo synaptic
``` Please post the outputted error messages in this thread, so that other people can help you figure out what's wrong.

---

### Post by Vivian-Synecdoche on 2008-05-22
> **N.N. said:**
> Sounds like you somehow broke gksudo, which is the graphical GTK+ front-end for su and sudo.

In order to diagnose why it won't start, launch it from the terminal and scrutinise the error messages that it outputs. Try starting Synaptic with gksudo, for instance: ```
gksudo synaptic
``` Please post the outputted error messages in this thread, so that other people can help you figure out what's wrong.

I'm not sure what I did - but after launching gksudo it started working. asked me for my password on gnome. 

I just tried launching the fromt he menu. It seems to work.

This was weird. It just wouldn't do this earlier today. Thank you for the trouble anyway.

---

