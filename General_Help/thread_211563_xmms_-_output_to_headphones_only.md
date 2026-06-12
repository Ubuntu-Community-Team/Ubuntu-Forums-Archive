---
title: "xmms - output to headphones only?"
date: 2006-07-08
forum: General Help
---

### Post by jms830 on 2006-07-08
Is there any way to make xmms output only to my headphones? I want to do this for DJing, as I'm using the amarok "headphone" script, which sends a song to play in xmms, but I still need to make xmms output to headphone only.  I have a Dell with the headphone jack in the front of the computer, and my soundcard is a Sound Fusion CS46xx (Turtle Beach Santa Cruz). I know I can change the output plugin in the preferences, but I've looked through and can't figure out where to go from here. With the OSS driver, I can output to a specific device in /dev, maybe one is the headphone? Thanks in advance.

---

### Post by vem0m on 2006-07-08
plug in ur headphones into ur computer directly where ur speakers normaly go is all i can think of :P

---

### Post by jms830 on 2006-07-08
the idea is that one song plays out of the speakers while I listen to another in the headphones, for DJing.

---

### Post by motin on 2006-09-29
Get the packages qjackctl (Jack) and mixxx (Mixxx DJ Software). 

It has what you want and much more. Please do read a Howto on how to use Jack as well, it will save you a lot of time. 

Basically you start Jack with qjackctl, and has to make sure before that esd is not running ("killall esd" in terminal) and that no other program is hogging the sound device (Skype, mplayer etc). 

XMMS has an output plugin for Jack as well in case you want it: xmms-jackasyn

---

