---
title: "Problems With Flash Player"
date: 2006-12-09
forum: General Help
---

### Post by gatorbowls on 2006-12-09
Looks Like when ever  i go to youtube.com and watch a video and then after watching it, i go to watch another 1 but than the sound doesent work. So i wait like a hour or so than it works..for the first video..but than when i try watching another video it did the same thing no sound... Whats up with this.

---

### Post by riven0 on 2006-12-09
> **gatorbowls said:**
> Looks Like when ever  i go to youtube.com and watch a video and then after watching it, i go to watch another 1 but than the sound doesent work. So i wait like a hour or so than it works..for the first video..but than when i try watching another video it did the same thing no sound... Whats up with this.

Gatorbowls, open the terminal and paste this:


> sudo apt-get install alsa-oss

Then:

> gksudo gedit /etc/firefox/firefoxrc

In the text file, change:

**FIREFOX_DSP=""** to **FIREFOX_DSP="aoss"**

Then restart the browser and see if it works.

---

### Post by taurus on 2006-12-09
It would be nice if you tell us whether you are using Breezy, Dapper, Edgy, or even Feisty!  Also, are you using flash 7 or 9???

---

### Post by gatorbowls on 2006-12-09
@riven0

IT worked..thanks soo much =]

---

### Post by strabes on 2006-12-10
you can also start progams with "aoss" in front of them like "aoss firefox" or "aoss rhythmbox" - it'll do the same thing.

---

### Post by riven0 on 2006-12-10
> **gatorbowls said:**
> @riven0

IT worked..thanks soo much =]

Glad to help. :mrgreen:

---

