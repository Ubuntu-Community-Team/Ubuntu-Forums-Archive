---
title: "Running 10.04 in a Chromium Kiosk Mouse pointer issues."
date: 2013-04-15
forum: General Help
---

### Post by scottdn on 2013-04-15
I have successfuly configured a 10.04 machine to run in a kiosk shell using Chromium.  The only issue I am running into is that the mouse pointer is displaying as a black X instead of the white pointer arrow.  If I allow the gnome environment to launch first then load the Chromium shell the mouse pointer appears correctly.  Is there any way to control how the mouse displays while in the Chromium shell?

---

### Post by mörgæs on 2013-04-15
Hi, welcome to the fora.

Is there a particular reason you are using a such old release?

---

### Post by scottdn on 2013-04-15
> **mörgæs said:**
> Hi, welcome to the fora.

Is there a particular reason you are using a such old release?

I was working off of a set of instructions that I found online and it was using 10.04.  It seems that 11.x + changed the environment and certain features like the Login Screen management was changed from 10.04 to newer versions.  

I am pretty new to Linux so I figured it would be best to stick with the same versions the instructions use.  If I could recreate the same environment in 12.x with the same ease as I was in 10.04 I would use 12.x but today I have had little success with newer releases.

What I need is a machine to auto login to a "Kiosk" session that uses Chrome as the shell.   Like I said it was considerably easier in 10.04 than it was in 12.04.

---

### Post by mörgæs on 2013-04-16
Yes, Ubuntu is hard to customise. Better to do a fresh install of Xubuntu 12.04.2 or 12.10 and try
[https://sites.google.com/site/easylinuxtipsproject/xfce#TOC-Safeguard-the-panels-kiosk-mode-](https://sites.google.com/site/easylinuxtipsproject/xfce#TOC-Safeguard-the-panels-kiosk-mode-)

---

