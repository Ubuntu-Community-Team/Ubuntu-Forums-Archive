---
title: "More Mouse Buttons"
date: 2007-02-10
forum: General Help
---

### Post by Steve- on 2007-02-10
I have a Logitech LX7 Cordless Laser Mouse and  LX710 Keyboard combo. The mouse has 2 standard buttons, a scroll wheel that clicks as the 3rd mouse button and has horizontal scroll, as well as 2 extra buttons for the purposes of back and forward.

Of course it works as soon as it's plugged in, but sadly only the 2 main buttons on the mouse work. How might I get at least the middle mouse button working as well? (Vertical scrolling works too)

I'm sure the special media buttons on the keyboard don't work either, but their low priority. However, if anyone knows how to get them working too, that'd be very helpful. :) 

Thanks,
  Steve

---

### Post by Rabbit_Alex on 2007-02-10
You should take a look at this thread.  

[http://ubuntuforums.org/showthread.php?t=332256](http://ubuntuforums.org/showthread.php?t=332256)

It worked for me because I have a Logitech MX610, which is what the thread talks about.  It might work for your LX7 though.  Give it a try and tell us how it works.

---

### Post by dagnabit dang doohickey on 2007-02-10
I think Rabbit_Alex meant to give this to you: [http://ubuntuforums.org/showthread.php?t=332256]("http://ubuntuforums.org/showthread.php?t=332256")

Here's a howto specific for the LX7. (it's in French, so I made the link a Google-translated link.)

[Mouse Logitech LX7, 9 buttons functional with my Ubuntu!]("http://translate.google.com/translate?hl=en&sl=fr&u=http://debuntu.free.fr/index.php%3F2005/12/11/493-souris-logitech-lx7-9-boutons-fonctionnels-avec-ma-ubuntu&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Dubuntu%2Blx7%2Bmouse%26hl%3Den%26client%3Dfirefox%26rls%3Dorg.mozilla:en-US:unofficial%26hs%3Dz6v%26sa%3DN")

---

### Post by Rabbit_Alex on 2007-02-10
Yeah I forgot to post the link when I replied.  I'm going to edit the post.  Thanks

---

### Post by Steve- on 2007-02-11
I have good news and interesting news.
The good news is that all my mouse buttons seem to be working.

The interesting news is that I haven't done anything yet. I started to read the French tutorial and got as far as "cat /proc/bus/input/devices" and noticed all the mouse keys had hex values. Sure enough, middle mouse pasted to the prompt.

Thanks anyways guys, i'll keep those handy in case it likes to break itself again :D

---

### Post by smellydog on 2007-02-24
What exactly did you do?  I also have the Lx7, and when i put in the
Option		"Protocol"		"evdev" 
anywhere in my "configured mouse" section in my xorg.conf file, X refuses to load.  Right now it is working basically with two buttons and the scroll wheel with the 
Option		"Protocol"		"ExplorerPS/2"
And it is plugged into my USB port, since i do not have a PS/2 installed on my laptop.

could you post what you did in your xorg.conf? or post a detailed walkthrough?

---

