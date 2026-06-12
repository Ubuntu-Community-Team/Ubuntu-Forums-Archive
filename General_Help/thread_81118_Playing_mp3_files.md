---
title: "Playing mp3 files"
date: 2005-10-23
forum: General Help
---

### Post by daditlefsen on 2005-10-23
Ive tried this command to get mp3 files playing on my Ubuntu:
> sudo apt-get install k3b-mp3

But when i open a mp3 file in XMMS i cant hear any sound.

---

### Post by Riverside on 2005-10-23
[QUOTE=daditlefsen]Ive tried this command to get mp3 files playing on my Ubuntu:


But when i open a mp3 file in XMMS i cant hear any sound.[/QUOTE]k3b-mp3 is an application related to the burning of MP3 files to CD, to the best of my knowledge.  The version of XMMS available by running apt-get install xmms plays MP3 files by default in my experience (Breezy & Warty, I wasn't able to play MP3 files using Hoary as with Hoary I was never able to get sound working at all).

Your difficulty sounds as if it may be an XMMS configuration issue.

---

### Post by xprisoner on 2005-10-23
You have to install gstreamer0.8-plugins. You can find it in Synaptic: Libraries(universe). 

Hope that helps.

---

### Post by Breaks on 2005-10-23
or it comes with amarok music player, which in my opinion is the better one of them all.

---

