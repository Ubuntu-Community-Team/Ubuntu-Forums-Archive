---
title: "How Do I Get 3D?"
date: 2007-08-15
forum: General Help
---

### Post by Mark76 on 2007-08-15
With my Nvidia Riva TNT2 card.

---

### Post by kdub432 on 2007-08-15
Thats a big question. There's lots of guides everywhere that describe how to do that, just dig around a bit before posting

---

### Post by Amazona aestiva on 2007-08-15
This works for me:
```
sudo apt-get install nvidia-glx
```

---

### Post by Mark76 on 2007-08-15
You are using an older Nvidia card, right?

---

### Post by AlexThomson_NZ on 2007-08-15
Thats a seriously old card- might be pushing it a bit

---

### Post by gobbles414 on 2007-08-15
If your using Ubuntu 7.04 (Feisty), you might be able to get it from the Restricted Drivers control panel. Also, you might try activating the Desktop Effects control panel to force a download of the needed drivers. Let us know if you are able to get your card working.

---

### Post by Mark76 on 2007-08-15
Erm... I'm using Gutsy :oops:

Hey... I wanted to get Gnash working.  Okay? :-\":

---

### Post by K.Mandla on 2007-08-15
> **Mark76 said:**
> With my Nvidia Riva TNT2 card.
Judging by this list, 

[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)

you need the nvidia-glx-legacy package, which is meant for early Nvidia cards. 

[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-legacy](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-legacy)

I don't think nvidia-glx or nvidia-glx-new will help you much. They don't play well with my GeForce2 440 Go either, and it's considerably newer than your Riva.

---

### Post by Mark76 on 2007-08-16
Yikes!  Dependency hell! :o

Which packages to I need to install?

---

### Post by UK-Wobbie on 2007-08-16
> **Mark76 said:**
> Yikes!  Dependency hell! :o

Which packages to I need to install?

Have a go on nvidia-glx-new :)
Thats works ok with Nvidia cards

---

### Post by K.Mandla on 2007-08-16
> **Mark76 said:**
> Yikes!  Dependency hell! :o

Which packages to I need to install?
Just install *nvidia-glx-legacy*, either in Synaptic or like this, in a terminal

```
sudo aptitude install nvidia-glx-legacy
```

Everything else should be dragged in with it, automagically. ;)

---

### Post by K.Mandla on 2007-08-16
> **UK-Wobbie said:**
> Have a go on nvidia-glx-new :)
Thats works ok with Nvidia cards
I really don't think that will work. I think you'll get an error message saying the driver doesn't support outdated cards. That's what I get when I try it on my Geforce2. Unless that has changed ... :-k

---

### Post by UK-Wobbie on 2007-08-16
> **K.Mandla said:**
> I really don't think that will work. I think you'll get an error message saying the driver doesn't support outdated cards. That's what I get when I try it on my Geforce2. Unless that has changed ... :-k

It may not work on Geforce2 but it works on my Nvidia card! It works better then the old one nvidia-glx :)

---

### Post by AlexThomson_NZ on 2007-08-16
I'm not sure if it's changed or anything, but from what I understand the *-legacy supports from TNT1 up.  The 'new' driver from the FX series and up.

So, again, try the legacy, and if you're lucky it will work.  The new drivers I seriously doubt will work

---

### Post by Mark76 on 2007-08-17
It''s odd because I defintiely had 3D on Dapper and (I think) Fiesty.

The problem is I can't remember how I got it.

---

