---
title: "Sound from more than 1 program at the same time"
date: 2007-07-04
forum: General Help
---

### Post by shiznatix on 2007-07-04
I am trying to play sound from more than 1 program at the same time. Basically I have a poker room running playing the sound effects but I would like to play a cd at the same time but the cd just goes without producing any sound.

How can I fix this?

---

### Post by Steveway on 2007-07-04
You have to use something like ESD or Pulsaudio for the output in all your programs.
They mix it together and send it to Alsa.
Thats not a bug!

---

### Post by shiznatix on 2007-07-05
> **Steveway said:**
> You have to use something like ESD or Pulsaudio for the output in all your programs.
They mix it together and send it to Alsa.
Thats not a bug!

I am aware that it is not a bug but how do I setup everything so that everything automatically plays sound even if something is already using the sound card?

---

### Post by shiznatix on 2007-07-06
_bump_

can anyone help me out with this one? I have googled for everything but I can't find a real answer.

---

### Post by luctor on 2007-07-06
System Menu -> Sound , enable ESD ...

I'm not in front of my ubuntu box .. so this one is out of my head ...

---

### Post by shiznatix on 2007-08-16
> **luctor said:**
> System Menu -> Sound , enable ESD ...

I'm not in front of my ubuntu box .. so this one is out of my head ...

This does not work. Although there seam to be times when it is able to play 2 sounds like when I am listening to music and playing a flash game the problems come when I am playing poker with a java applet. The applet makes some sounds every now and then and if I am switching between a track on my mp3 player, the mp3 player loses its sound. Its like they compete for the sound card and the first one to get it wins.

How can I go about fixing this so that no matter what, I can play sound through whatever I want?

---

### Post by ibanez88 on 2007-08-26
I just want to confirm this issue.  I have esd enabled and still can't get sound out of firefox and xmms at the same time.  If they are both open, I have to quit both apps and reopen the app that I want to get sound from.  The same can be said for totem or any other app that uses sound as far as I can tell.  I tried setting all of the options in the devices tab under Sound Preferences to esd (and also to ALSA), but I can confirm that changing these settings does not get it working with my hardware (Digigram VXPocket V2 on a Toshiba Satellite 5105-S701).

---

### Post by Grigorius on 2007-09-06
bump

---

### Post by SomethingUniqueHere on 2007-09-06
Ugh, i have this too, it's very irritating.  Anyone know a fix?

---

### Post by joo8111 on 2008-04-17
I using Virtualbox for Windows XP.
When I started Virtualbox, sound system doen't work any more.

Ubuntu 8.04 use pulseaudio. but my Virtualbox use ALSA Driver.
this is problem.

I make Virtualbox use pulseaudio.
Now, sound system works.

Check your program.

-----
Sorry, I can't speak English well. :-)

---

### Post by Trail on 2008-04-17
Make sure you have selected ALSA as your default sound system. I don't remember where exactly this is, since I use KDE, but should be somewhere under Sound.

---

