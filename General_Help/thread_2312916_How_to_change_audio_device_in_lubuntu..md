---
title: "How to change audio device in lubuntu."
date: 2016-02-08
forum: General Help
---

### Post by arthur24 on 2016-02-08
I've been trying to configure Lubuntu today, and haven't touched the operating system alot since I started using it.
I found out I could use Alsamixer to change audio settings in Lubuntu. 

By default the audio is broadcasted through the green audio jack socket on which my headphone is connected.
I also have a Onkyo HT receiver that is connected with a HDMI cable to my computer. It worked fine in Ubuntu. That's probably because Ubuntu had a build in audio menu.

I tried to fiddle the knobs in Alsamixer, but now I can't get any sound whatsoever.
I tried to press F6 to see if a receiver of some kind got mentioned in the menu. But it only lists default, HDA intel PCH, HD webcam C525, HDA Nvidia and a option to enter a device name.
I tried all but the last option to see if I could get sound through any other device or port, but that didn't work.

Even worse, I tried to revert back to the default sound card, on which the headphones used to work.
They also stopped working.

I now get a very annoying completely random low volume beep through my headphones. sometimes several in a row.
 
I hope you guys and gals can help me out with this.

---

### Post by ajgreeny on 2016-02-08
You will find moer configuration options available if you install **pulseaudio** and **pavucontrol** neither of which are in the default install of Lubuntu.

That should allow you to choose the output device you want.

---

