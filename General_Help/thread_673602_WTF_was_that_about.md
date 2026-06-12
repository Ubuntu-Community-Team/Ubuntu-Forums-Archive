---
title: "WTF was that about?"
date: 2008-01-20
forum: General Help
---

### Post by Lord Xeb on 2008-01-20
I did a full system update (there were 173 updates to install). While I was trying to checkout some other software, I started to get a syntax error....WTF? so I restarted, and I got an error as soon as Gnome started to load and it started as default setup. I restarted and had no problem (apparently it was something to do with daemon or something an getting disconnected from the internet)

---

### Post by Bodsda on 2008-01-20
it was probably a file trying to update while you were looking/opening it ,.,. to my knowledge sync error means syncronicity error which i beleive is when a program gets a result it wasnt expecting. if it wants to write to a file and u have it opened it cannot write to the file, hense the error,.,. the error after reboot was probably telling you there was an error during the update, and since it has already told u there was an error it feels no need to tell u again. ,.,. or at least thats wot i think it is,.,.lol,.,.

---

### Post by family on 2008-01-20
Hey Lord.
Ubuntu is Debian, and it uses something called apt (advanced package tool) to install, upgrade, and generally maintain all of normal users software.
Two processes may not use it at once.
The update manager was using it.
Then you tried installing/removing stuff with the add/remove programs applet or GDebi, w/e.
This was the 'WTF'.
The daemon in question is the update manager.
Open up a terminal and type 'sudo apt-get update && sudo apt-get upgrade' and leave it open to finishe the process.

Oh, and don't use the acronym, 'WTF'; it's immature and makes people ignore you.

---

### Post by steveneddy on 2008-01-20
I wonder if you could use less "language" and actually tell us what was going on with the PC.

What did the error say?

What were you doing, exactly, when the error occurred?

What happened to get you disconnected from the internet?

---

