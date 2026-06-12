---
title: "Creox error... grr...."
date: 2007-04-01
forum: General Help
---

### Post by Drate on 2007-04-01
BTW, I have asked this before and after a couple of days got absolutely no response.  I still believe that Ubuntu community is the best tech support ever, so I hope this does not break forum etiquette to repost it here in General Help, this isn't to get a "faster response" like the Readme's say not to... it's to get ANY response. :D

Truly, i've yet to ask a question that yall couldn't answer and I appreciate it much, so here tiz:

I am running Ubuntu Edgy + the Kubuntu Desktop installed. I downloaded Creox, I plugged my stuff in, and I got what evidently is a fairly common problem: when I hit Play it gives me a very detailed error... it says exactly this: "Error".

Informative right? I've tried it both in KDE and GNOME. So I have seen this one person saying something about starting it with a bit of terminal command involving this command "jackd" and I tried that and it said there is no "jackd" command.  I then installed jackd and tried the command over again to same results... "Error:"

So yeah... it'd really be cool if someone could help me out!

---

### Post by zvacet on 2007-04-02
Did you downloaded all dependencies(mark with red ball)with the package?If not do it and if you still have problems,just ask.

---

### Post by Drate on 2007-04-02
They are all there, just checked everyone.  Some of them are updated versions but they are all there.

---

### Post by barlaso on 2007-04-23
Well, you need to install jack, (if you havent done so already).  Then you need to open a terminal and start a jack server by using something like:

```
jackd -d alsa
```

---

### Post by tjk on 2007-04-30
> **barlaso said:**
> Well, you need to install jack, (if you havent done so already).  Then you need to open a terminal and start a jack server by using something like:

```
jackd -d alsa
```

The error message problem is solved with this suggestion, but I still don't get any effects...

---

### Post by Placenta Juan on 2007-05-07
Same problem here: error message until I ran the jackd command, but still no effects. Somebody out there has to have gotten this to work?
I'm using Kubuntu Feisty

---

