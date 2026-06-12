---
title: "Any Ubuntu/Linux Graphics/Display speed test programs?"
date: 2007-01-15
forum: General Help
---

### Post by emarkay on 2007-01-15
I can find a few programs for DOS and Windows that will display the refresh and FPS speeds of my graphics card - in both 2D and 3D mode.

But I can not find anything similar for Ubuntu\Debian\Linux.

This seems to be the most comprehensive collection of sites, but alas nothing for Linux:
[http://www.benchmarkhq.ru/english.html?/b_e.html](http://www.benchmarkhq.ru/english.html?/b_e.html)

Anyone have one, maybe from a game test, or a development program, or maybe a stand alone .deb file - or even better, one that runs the same tests in both Linux AND in a Windows environment?  :)

THANKS!

---

### Post by crispy_420 on 2007-01-16
glxgears in terminal. also you can run glxgears -printfps too

---

### Post by ardchoille42 on 2007-01-16
I was told by many people that glxgears is not a proper benchmarking too and to not rely on its output.

---

### Post by emarkay on 2007-01-16
> **ardchoille42 said:**
> I was told by many people that glxgears is not a proper benchmarking too and to not rely on its output.

OK, well what alternatives do you suggest?

Anyone else?

---

### Post by crispy_420 on 2007-01-18
It at least tells you that you have your basic graphics card setup. Going from 400fps to 1900fps is a good enough benchmark for me

---

### Post by mcduck on 2007-01-18
The only real test would be running some game's benchmark mode. Many 3D games have something like that and that's the way to go.

Glxgears is only good for telling if you have any 3D-acceleration at all. There's a reason why the '-printfps'-option was disabled for long time and you had to run 'glxgears --iacknowledgethatthistoolisnotabenchmark' to get the fps output ;)

---

### Post by crispy_420 on 2007-01-18
A few games do have benchmarks built in. Look at Doom and Quake, mainly id games.

---

### Post by bwhite82 on 2007-01-29
I am suggesting that everyone use, UT2004+UMark. The reason for this is so that we can have a *common* benchmark to go off of. I know many people like to make the argument that we cannot reliably benchmark video cards in Linux, "too many variables", they say. While this is true, we can get "close enough" with one standard benchmarking program.

I would actually like to see a wiki page made with benchmark scores from various cards, what driver their using, etc. So that a new Ubuntu user can just go there, get a ballpark figure of where his FPS should be at and go from there. It would be a time-consuming project, which is why I am hesitant to go forward with it.

---

### Post by orb9220 on 2007-01-29
So what everyone is saying if I want to know how my graphics subsystem is fairing.
I have to install and run a Game?

Where's all the great graphic tools for testing Xserver,Gnome.etc...?

---

### Post by Jussi01 on 2007-01-29
Was there not one integrated into beryl? I think i remember reading that somwhere...

EDIT: does this site help at all?

[http://lbs.sourceforge.net/](http://lbs.sourceforge.net/)

---

