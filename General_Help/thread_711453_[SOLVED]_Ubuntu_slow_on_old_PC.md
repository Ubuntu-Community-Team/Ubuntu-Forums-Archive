---
title: "[SOLVED] Ubuntu slow on old PC"
date: 2008-02-29
forum: General Help
---

### Post by iheartubuntu on 2008-02-29
I talked my sister into putting Ubuntu on her old laptop so she could get a feel for it before we install it in on a new laptop she will be getting.

The old laptop is a PIII-700mhtz with about 250mb of RAM and 11gb HD.

I installed Ubuntu 7.04 Feisty (Canonical CD) and Ubuntu seemed slow. It still works. I updated the 190 or so updates (250mb worth) and rebooted and the computer seems a little faster but is not as fast as her XP that was on this system. 

She is sort of complaining :) Truth is she never used the computer at all and had nothing on it but XP and a few photos.

Is there anything I can do to speed things up for her right now (short of buying another memory chip)? She'll be using this old system for Firefox mostly to check email for the next week until her new system arrives.

Thanks!

---

### Post by pointone on 2008-02-29
With only 256 MB of RAM, you might want to consider using a less memory-intensive desktop environment like Xfce or Fluxbox.

---

### Post by oldos2er on 2008-02-29
Maxing out the RAM would no doubt help; but for now I'd try a lighter distro, e.g. Vector Linux.

---

### Post by RedSquirrel on 2008-02-29
As suggested above, you might want to look at the Xfce desktop environment. The package name is **xfce4**. It's in the repositories.

Using a window manager instead of a full desktop environment might be even better (fluxbox, icewm, openbox...).

If you want maximum speed, build up from a minimal installation:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by kge420 on 2008-02-29
I'm running VectorLinux 5.9 on a similarly equipped machine. No problems.

---

### Post by Jay Jay on 2008-02-29
As with the other posts, I'd suggest switching to a lighter distro or desktop environment - I use Xubuntu on a machine with a similar spec to yours and speed wise it runs quite well.

---

### Post by zoomzoomzoom on 2008-02-29
Puppy is my regular everyday operating system.  Can recommend it.  Runs decent on anything that win98 runs on from P1 up.  I was actually surprised when I put it on an old 300mhz laptop with only 32mb ram.  It did ok, though Seamonkey and Firefox wouldnt even load with that small amount ram.  Opera did ok though, you just didnt want to open lot tabs.  Its pretty easy to overwhelm 32mb ram with modern software.  128mb ram and Puppy is in high cotton though I run with 256mb cause it was cheap enough, cant see any benefit to more though.  

As live cd also noticed PClinuxOS is faster than Ubuntu.  Personally I dont really care for the bloat of KDE or Gnome, but each to their own.  Fast trumps pretty in my book every time.  And you want to see pretty and light, take look at Puppy 2.15CE.  It was community edition all prettied up.

DamnSmallLinux and Austrumi Linux also small and fast, I just find Puppy friendlier.  As I say, each to their own.

---

### Post by a94060 on 2008-02-29
i got xubuntu on my 466mhz and 256 mb ram box. It should be what you would like if you want to stick to ubuntu based. It runs pretty fast and looks cool also :)

---

### Post by sstusick on 2008-02-29
Just install Xubuntu onto that machine...that should make a difference.

In a terminal type "sudo apt-get install xubuntu-desktop."

---

### Post by iheartubuntu on 2008-03-01
> **sstusick said:**
> Just install Xubuntu onto that machine...that should make a difference.

In a terminal type "sudo apt-get install xubuntu-desktop."

Thanks for the advice in here! On monday I'll load up xubuntu for her!

---

### Post by iheartubuntu on 2008-03-06
> **sstusick said:**
> Just install Xubuntu onto that machine...that should make a difference.

In a terminal type "sudo apt-get install xubuntu-desktop."

Is that all that I have to do? I did this, it downloaded and installed everything (about 60mb, expanded to 300mb) but when I rebooted the system still looks and acts just like Ubuntu, not Xubuntu.

Any tips?

---

### Post by foresto on 2008-03-06
Log out, and when the login screen appears, select "xfce session" from the "session" menu before logging in again.

---

### Post by iheartubuntu on 2008-03-06
> **foresto said:**
> Log out, and when the login screen appears, select "xfce session" from the "session" menu before logging in again.

It worked! Thanks so much!

---

