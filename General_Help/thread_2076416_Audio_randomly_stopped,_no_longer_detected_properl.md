---
title: "Audio randomly stopped, no longer detected properly"
date: 2012-10-26
forum: General Help
---

### Post by LukeLinux on 2012-10-26
So I've been running Ubuntu 12.04 for a few weeks now, and I upgraded to 12.10 the day it released, and up to now I've been having no problems with it. However, today something weird happened. I was experimenting with running a Windows program in WINE, when suddenly I noticed that I couldn't hear anything anymore. I figured it was just a temporary glitch, so I ALT-F2'd into a terminal and restarted GDM. Everything was normal again, sound was fine. But then I rebooted because I needed a real Windows install for a few minutes, and when I came back into Ubuntu, sound just failed to detect my hardware properly. Rebooting again and restarting GDM had no effect. It's not totally broken, as I can listen through my bluetooth headphones just fine, but my internal sound device is not working at all.

What previously was detected as "Realtek HD Audio" or something along those lines is now detected simply as "Built-in Audio Analog Stereo", and no sound comes through using it. I also don't have the option to select "Stereo Audio Duplex" or any level of surround sound. Mic input is also not working. :confused:

To my knowledge, I didn't touch anything that should affect sound today, so I'm totally baffled as to why this would have happened. I've had sound issues with Linux in the (distant) past, but my 'fixes' were really hack jobs that only worked well enough to hold me out until a proper update was released, so I have no idea where to even start with fixing this. Any help would be appreciated.

---

### Post by LukeLinux on 2012-10-26
Forgot to mention, I am running a custom built PC with a GIGABYTE 890XA mobo, which is my sound device (ALC892 codec).

If I could just completely reset sound in Ubuntu I think that would solve my problems, but I'm all ears if an easier fix is possible.

EDIT: Well now this is very strange. After posting this, sound magically came back again! Input and output both are suddenly working and all the configuration options are back. But why does it cut out and come back so randomly? Any thoughts?

---

