---
title: "Totem Player shuts down when playing .mov files transferred from camera SD card."
date: 2008-06-15
forum: General Help
---

### Post by qphone on 2008-06-15
Hello,

Firstly, I do in fact have the proper codecs (at least to my newbie knowledge) because I can go to apple.com/trailers and firefox plays all their trailers .mov files without a problem

So my question is...I've transferred a bunch of .jpeg's (plays fine) and .mov's (doesn't play) into /home/sony/Pictures/Panasonic Pictures and Videos/June 15, 2008 folder

**How come when I double click on a simple .mov file, Totem movie player opens up and then shuts off?**

Is there any way to watching a simple .mov files that's on my hard drive? I love ubuntu in the short time I've had this but something this simple is so aggravating!

---

### Post by prince_niceguy on 2008-06-16
install vlc player from the repos... i have found it more stable and having more features compared to totem...

---

### Post by geirha on 2008-06-16
This certainly sounds like a bug in totem. If you have the time, it would be nice if you reported this bug at [https://bugs.launchpad.net/totem/+bugs](https://bugs.launchpad.net/totem/+bugs). Supplying a sample .mov-file that makes totem crash should make it fairly easy for the developers to find and fix the problem.

---

### Post by amir1 on 2008-06-16
> **geirha said:**
> This certainly sounds like a bug in totem. If you have the time, it would be nice if you reported this bug at [https://bugs.launchpad.net/totem/+bugs](https://bugs.launchpad.net/totem/+bugs). Supplying a sample .mov-file that makes totem crash should make it fairly easy for the developers to find and fix the problem.

its not only totem. mplayer shows same behavior. I wasnt able to fix this problem. my guess is w32codec has some problems. for me everything was working fine prior to hardy

---

### Post by geirha on 2008-06-17
mplayer usually gives meaningful messages about why it won't play it. Could you paste the terminal output of mplayer? ```
mplayer sample.mov
```

---

