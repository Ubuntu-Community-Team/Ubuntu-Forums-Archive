---
title: "Gnome Problem Please Help"
date: 2008-03-11
forum: General Help
---

### Post by TheMixtureMedia on 2008-03-11
Hi there I just downloaded a update and it looks like it delete my desktop (gnome) i can get to were it ask me for the password for my wifi but there is nothing on the screen and that is after i did a update today can someone please help me fix this i have alot on my computer and do not want to lose this.

---

### Post by Het Irv on 2008-03-11
Can you get to a terminal?
Do you remember what the update was? (the last update I did was a python update)
I am not sure what to do for you, but if you get to a teminal you might be able to uninstall/reinstall gnome.

---

### Post by TheMixtureMedia on 2008-03-11
I can not get to any terminal on the screen just the wifi password comes up and thats it :-( nothing else but the mouse and it was a update for 8.04

---

### Post by TheMixtureMedia on 2008-03-11
I can get to root is that as good as terminal please some one help :-(

---

### Post by Het Irv on 2008-03-11
Let me check my commands, hang on a sec.  I don't want to give you bum info.


```
sudo aptitude remove ubuntu-desktop
sudo aptitude purge ubuntu-desktop
sudo aptitude install ubuntu-desktop
```

The first line will uninstall Gnome
the second will clear all the settings
and the third will reinstall it.

I would wait a bit before running these commands in case someone knows of a better way, or knows that my way will harm your computer.

---

### Post by TheMixtureMedia on 2008-03-11
thank you for you help :-)

---

### Post by TheMixtureMedia on 2008-03-11
It comes up and says 
sudo: unable to resolve host

any ideas why it is saying that??

---

### Post by Het Irv on 2008-03-11
It may be because you are logged in as root, try the commands without sudo.

---

### Post by TheMixtureMedia on 2008-03-12
nope nothing and i tried what you wrote twice and it went through some stuff and I still do not have my desktop can someone please help me i have pictures of my kids on there i do not want to lose :-(

---

### Post by TheMixtureMedia on 2008-03-12
anyone please :-(

---

### Post by TheMixtureMedia on 2008-03-12
Can anyone out there please help me this is what I can get I can get my mouse, when i press ctrl alt delete it comes up with that screen and it comes up and promtes me for my wifi passwrod but I do not have anything on my desktop its like the gui is gone and it happened after i did a update :-(

---

### Post by Het Irv on 2008-03-12
I don't think that it is a problem with your Xserver because you do get a prompt for your Wifi and you get a mouse.  I am not sure how to, to get your current computer working you need to reinstall Gnome.  If you just want to get the files off your computer you can use the LiveCD to access the hard drive.

---

