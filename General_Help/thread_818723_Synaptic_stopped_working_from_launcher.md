---
title: "Synaptic stopped working from launcher"
date: 2008-06-04
forum: General Help
---

### Post by scope on 2008-06-04
Hi, first of all, I am quite new in linux world, I've tried several distros but for a very small amount of time, and I always ended deleting them because I didnt use them. By the way, I'm spanish so excuse me for the english.

I installed the new ubuntu 8.04 yesterday on my laptop and I was very amazed with the wubi windows installation, so I gave it a try and installed it from vista. I installed wine, amsn, eclipse and ran World of Warcraft from wine.
When I exited warcraft, I noticed that synaptic wouldnt load from the icon I got on the upper menu bar, neither from the launcher inside the upper menu (system - administration). The thing is that if I started it from a terminal using synaptic command, it would start flawlesly.
The other thing I noticed that was failing was the Update manager. It got stuck on getting new updates.

Today I reinstalled ubuntu, this time not from wubi but in an independant and bigger partition. I have installed the same: amsn, eclipse, wine. I ran world of warcraft and I have, again, noticed that synaptic isnt working from the launcher and update manager gets stuck.

By the way, if I go to the processes monitor and I kill the 4-5 processes called "gksu", the update manager seems to start working again.

Also, restarting doesnt fix the problem.

Any help would be very appreciated :)

Thanks


Edit: I found the solution, it is a very stupid thing. I have found this thread [http://ubuntuforums.org/showthread.php?t=816708&highlight=synaptic]("http://ubuntuforums.org/showthread.php?t=816708&highlight=synaptic") and I followed the tip from buntunub and now everything works ok. I had 127.0.1.1 computername.DOMAIN in the hosts file and I changed it by computername only.
Sorry for the thread.

---

