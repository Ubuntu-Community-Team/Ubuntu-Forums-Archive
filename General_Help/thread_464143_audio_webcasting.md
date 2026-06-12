---
title: "audio webcasting"
date: 2007-06-04
forum: General Help
---

### Post by alek66 on 2007-06-04
What programs or websites can you recomend me for audio(mp3) webcasting.
I want to make a local "radio" for my friends... I want to be able to cast my mp3 selections.
I installed internet dj console, but keeps crashing. And gnome peer cast, doesnt seems to work if i am using a wifi conection.

---

### Post by defishguy on 2007-06-04
This is the app that I've seen used most. [ICECAST]("http://www.shoutcast.com/")

---

### Post by alek66 on 2007-06-05
Is it hard to configure?
I'm a complete newbie here, does it cast... what I hear on xmms?

---

### Post by alek66 on 2007-06-05
i installed it and I cant make it work. I also installed the xmms plugin
> alek@DeathStar:~$ icecast
[05/Jun/2007:18:35:55] No configfile found, using defaults.
Icecast Version 1.3.12 Initializing...
Icecast comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of Icecast under the terms of the
GNU General Public License.
For more information about these matters, see the file named COPYING.
Starting thread engine...
[05/Jun/2007:18:35:55] Icecast Version 1.3.12 Starting..
[05/Jun/2007:18:35:55] Starting Admin Console Thread...
-> [05/Jun/2007:18:35:55] Starting main connection handler...
-> [05/Jun/2007:18:35:55] Bind to socket on port 8000 failed. Shutting down now.
-> [05/Jun/2007:18:35:55] Cleanly shutting down...
-> [05/Jun/2007:18:35:55] Closing all listening sockets...
-> [05/Jun/2007:18:35:55] Telling threads to die...
-> [05/Jun/2007:18:35:55] Closing sockets for admins that keep hanging around...
-> [05/Jun/2007:18:35:55] Closing sockets for sources that keep hanging around...
-> [05/Jun/2007:18:35:55] Closing all remaining sockets...
-> -> [05/Jun/2007:18:35:55] Waiting a wee while to let the other threads die..
-> [05/Jun/2007:18:35:58] Ok, that's enough, let's kill the remaining 1 bugger
-> [05/Jun/2007:18:35:58] Closing and removing directory servers...
-> [05/Jun/2007:18:35:58] Removing remaining sources...
-> [05/Jun/2007:18:35:58] Exiting..


---

### Post by CocoAUS on 2007-06-05
Why not just set up a music streaming server instead?  I suggest gnump3d.  Just install it, then edit the configuration file to point it to your library, and make sure your router is set to allow people in on that port.  They can change the look of the interface, make their own playlists, etc, instead of having to listen to your preset "radio" playlist.

---

