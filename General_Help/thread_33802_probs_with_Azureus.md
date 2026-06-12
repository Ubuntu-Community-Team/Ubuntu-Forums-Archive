---
title: "probs with Azureus"
date: 2005-05-12
forum: General Help
---

### Post by maltje on 2005-05-12
Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.
What is did?

---

### Post by codejunkie on 2005-05-12
[QUOTE=maltje]Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.
What is did?[/QUOTE]

Please explain in detail what the problem is, are you trying to install Azureus the java based bittorrent client and this error occurs or does this happen when you try and run Azureus. and being that Azureus is a java based bittorrent client with no integrated media player I think but i could be wrong, it shouldn't be affecting the sound server at all so it may be something completely unrelated to Azureus causing the Sound Server errors .

---

### Post by maltje on 2005-05-12
I got this error while shutting down azureus!!!!!!!!!!!!!!
After that the sound isn't working anymore.
After reboot everything is fine as long as i don't stop azureus.

---

### Post by DutchLau on 2005-05-12
Did you follow [these](http://ubuntuguide.org/#configuresoundproperly) directions yet?

See if that solves your problem (you don't necissarily need to Uncheck "sounds for events" if you don't want to) otherwise try "sudo killall esd" before you try shutting down Azureus and see if that solves the problem. Tell use what happens!  :razz: 

Good luck!

DutchLau

---

