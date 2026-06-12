---
title: "programs take forever to open"
date: 2006-11-17
forum: General Help
---

### Post by no angel on 2006-11-17
Hi all,

Two edgy machines I look after have this problem where apps take way too long to load. The cursor changes to the please wait cursor, and a "starting whatever" entry appears in the window list. It stays there for about 10 - 15 seconds before the app loads. When I log in the splash screen hangs around for ages too. Anyone else experiencing this?

---

### Post by ciscosurfer on 2006-11-17
Which apps?  The system in general?

---

### Post by no angel on 2006-11-17
> **ciscosurfer said:**
> Which apps?  The system in general?

Everything. One of the machines only behaves like this when I use a particular monitor, but the other one does it always. I've tried reconfiguring xserver-xorg on both, different display drivers, etc. Nothing seems to work. I find it hard to believe that I've seen this on multiple machines and nobody else has...

---

### Post by taurus on 2006-11-17
Well, the spec of your machines would be nice and which version of Ubuntu are you running!

---

### Post by no angel on 2006-11-17
> **taurus said:**
> Well, the spec of your machines would be nice and which version of Ubuntu are you running!

The specs of the machines aren't important because Dapper worked fine on both. Edgy is on both now, and both have this weird slowdown problem. Honestly, nobody has seen it?

---

### Post by chimera007 on 2006-11-19
I have the same problem. I think they don't reply because you were rude. :) 

Well i will tell you my system specs: 3.0Ghz Intel Pentium Prestcot, Gefore 6600 256MB, 786MB Ram, 20GB HDD partition, 900 Swap (what was left :) ). Over all it is a very fast computer on Window. I am using my laptop that doesn't even have half of any of my desktop specs, while writing this. The laptop out preforms the desktop, even though my desktop has better specs.

Weird eh? So i was wandering what was the slow down about. I am going to reinstall anyways. I don't have the patience to way a few hours.

---

### Post by richardspirit on 2006-11-19
I'm having the same problem

I am running a 1.7ghz amd 512 Ram

Everything was perfect on Dapper now it is running slower than my windows box which is very bad...

---

### Post by richardspirit on 2006-11-19
sorry and Geforce 4, 160 GB HDD

---

### Post by Gorgonzola on 2007-02-13
I'm not sure if this is related but I'll share my experience with you anyway just in case.

When I installed Edgy on my main system (I had only used Ubuntu on my old PC in the past), I was initially disappointed at the overall responsiveness of Edgy. I was expecting it to be so much faster than my old machine (which it was in Windows).

When I installed the Nvidia drivers (my card is a Nvidia 6600GT), **everything** began responding much faster. The Ubuntu splash screen now flies past, all the menus in Gnome are instant, and all my applications seem to load much faster too.

It may sound a little far-fetched, but to me it seemed like alot of the system was slow because it was waiting on the video card running on the sloppy default drivers.

If any of you are running Nvidia cards and haven't yet installed the proper drivers, I recommend trying it and seeing if it makes an improvement.

---

### Post by pppetter on 2007-02-13
I didn't notice any big difference between dapper and edgy, except for bootup which was faster :)
Although I later on decided to try kubuntu, which I now run as primary - kubuntu actually FEELS faster than ubuntu - which is weird becouse it's quite bloaty in my opinion. :P

But anyways. Have you people installed some servers or Beryl and stuff like that? That takes some resources you know.

---

### Post by kerry_s on 2007-02-13
> **no angel said:**
> The specs of the machines aren't important because Dapper worked fine on both. Edgy is on both now, and both have this weird slowdown problem. Honestly, nobody has seen it?

Did you upgrade or is this a fresh install?
Also can you post your /var/log/xorg.0.log ?

---

