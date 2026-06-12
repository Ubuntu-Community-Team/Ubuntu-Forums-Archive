---
title: "Am I missing a package? Which one?"
date: 2007-05-05
forum: General Help
---

### Post by Zalbor on 2007-05-05
It seems that in order to run a program I have with sound, I need the file /dev/snd/midiC0D0 .
According to the error output ("ALSA lib rawmidi_hw.c:233:(snd_rawmidi_hw_open) open /dev/snd/midiC0D0 failed: No such file or directory") it seems that this file is a part of ALSA.
Searching for the file's name in these forums, I found out that other seem to have it. Is it in a package I've not installed? Which one, if that's the case?

---

### Post by baka_rob on 2007-05-11
Which program are you trying to use?  Which sound card are you using?  Does sound work **anywhere** in your system?

From googling around a little bit: /dev/snd/midiC0D0 is a file that would be created by a sound driver.  Are there any packages specific to your sound card that are in the package list?  Or some midi package that you might need (since it's apparently trying to use some midi functionality)?

---

### Post by akudewan on 2007-05-12
Try following this Howto: [http://ubuntuforums.org/showthread.php?t=58859&highlight=Midi+Howto](http://ubuntuforums.org/showthread.php?t=58859&highlight=Midi+Howto)

---

### Post by Zalbor on 2007-05-26
Sorry for taking so long to reply, I had forgotten about this thread.
I have sound pretty much everywhere except this thing: The Adventure Game Studio engine. It used to work fine in edgy, but now it complains about this missing file.

---

### Post by akudewan on 2007-05-27
This program you're using needs midi support to play sound. Did you try that howto I posted earlier ?

---

### Post by Zalbor on 2007-05-27
Actually no... I'm thinking that since I had no such problem in edgy and I definitely hadn't done things like those the howto says, there must be an easier way...

---

### Post by akudewan on 2007-05-27
> **Zalbor said:**
> Actually no... I'm thinking that since I had no such problem in edgy and I definitely hadn't done things like those the howto says, there must be an easier way...

You do have a point. Maybe the solution is simply installing or reconfiguring some alsa package. I'm not sure which one, but check if alsa-utlis is installed.

Hopefully someone can shed more light on this.

---

