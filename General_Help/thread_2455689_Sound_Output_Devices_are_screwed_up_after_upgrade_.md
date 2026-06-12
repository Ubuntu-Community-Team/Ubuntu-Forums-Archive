---
title: "Sound Output Devices are screwed up after upgrade to 20.04"
date: 2020-12-25
forum: General Help
---

### Post by Old Jimma on 2020-12-25
HI Community:

I just upgraded to 20.04. It is nice.

It seems that the sound output devices are found... but the list at Settings > Sound > OUtput Device is screwed up: the list is there but the devices do not correspond to the actual devices... and some do not work.

How do I fix this?

THanks,
Old Jimma

---

### Post by qhartman on 2020-12-29
I am having similar issues going from 18.04 to 20.04 and now 20.10. All my audio devices show up in my device selection list, but no matter which one I choose, audio only ever comes out the built-in speakers on my laptop

---

### Post by qhartman on 2020-12-29
Huh, I just did some tinkering around with `pactl`, and now the situation is even weirder. Everything seems to be using the correct output now _except_ the test sound in the Gnome control panel. Browser sounds, system bell, games are all using the output I set, it's only the test sound that is stuck coming out the built in speakers... weird...

---

### Post by Old Jimma on 2020-12-30
Hi  qharman:

Thanks for your comments.

It may be useful to know that I upgraded from 18,04 to 20.04 with the automatic upgrade system... something like sudo apt-get upgrade.... or something like that. I did my installation after consuting with the forms on how to prepare for this sort of installation... and followed the advice from the forums to disconnect ppas and make the installation look as much like a de novo installation as possible.

The more I worked with the installation of 20.04, I found  more quirky and dysfunctionalities with the resulting 20.004 installation. For example, OpenOffice would not work at all.

I struggled with it and some old hardware at the same time to get it all to work.

**Then, just installed 20.04 from a start-up disk.... and all of those problems disappeared.**


Now, life is good and has gone back to normal. Ubuntu 20.20 works nicely and has enhancements that I appreciate!

Old JImma

---

### Post by qhartman on 2020-12-30
Thanks for the data point Old Jimma! I've been wondering if a clean install would fix my issue as well, but I really like to know why things like this happen and get to root causes if I can. I may just do a nuke and pave though!

---

