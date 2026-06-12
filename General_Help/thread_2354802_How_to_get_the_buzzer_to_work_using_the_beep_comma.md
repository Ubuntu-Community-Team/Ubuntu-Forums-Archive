---
title: "How to get the buzzer to work using the beep command?"
date: 2017-03-06
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-06
How to get the buzzer to work using the beep command after an especially long process as talked about here: [https://askubuntu.com/questions/19906/beep-in-shell-script-not-working](https://askubuntu.com/questions/19906/beep-in-shell-script-not-working)
What I tried so far:

After installing the beep command by typing:

```
sudo apt-get install beep
```

I typed:

```
sudo modprobe pcspkr
```

to no avail. I even tried editing /etc/modprobe.d/blacklist.conf and commenting out blacklist pcspkr and restarting, still doesn't work. I'm under Ubuntu 16.04 LTS. I'm on a laptop, if that matters.

---

### Post by vasa1 on 2017-03-06
Is this thread not a continuation of the one you have here: [No Beep Sound When Typing \a]("https://ubuntuforums.org/showthread.php?t=2353551")?

---

### Post by John_Patrick_Mason on 2017-03-06
> **vasa1 said:**
> Is this thread not a continuation of the one you have here: [No Beep Sound When Typing \a]("https://ubuntuforums.org/showthread.php?t=2353551")?

No. That thread was to get the *terminal** bell* to work. This is to get the buzzer to work when using the beep command. Completely different. Different sound, too. The reason I want to use the buzzer to alert me when an especially long process is finished is because the terminal bell sound is very brief, and is something you could easily miss when away from your computer.

---

### Post by vasa1 on 2017-03-06
In that case, you could also look at visual cues. A default .bashrc has an "alert" alias. There are AU q-n-a's related to that:
[http://askubuntu.com/questions/748860/how-can-i-use-the-eos-terminal-notification-in-ubuntu](http://askubuntu.com/questions/748860/how-can-i-use-the-eos-terminal-notification-in-ubuntu)
[http://askubuntu.com/questions/611874/how-do-you-make-your-terminal-play-a-sound-or-offer-a-notification-when-it-has-f](http://askubuntu.com/questions/611874/how-do-you-make-your-terminal-play-a-sound-or-offer-a-notification-when-it-has-f)
and more

BTW, I gave up on getting any sound via beep or buzzer. If I do want a sound, I chain```
mplayer -really-quiet /home/vasa1/Dropbox/Sounds/alarm-clock-elapsed.oga
```or any other audio file I like.

---

### Post by John_Patrick_Mason on 2017-03-06
If that's the case, how do I completely remove beep?

---

### Post by vasa1 on 2017-03-07
> **John_Patrick_Mason said:**
> If that's the case, how do I completely remove beep?

Just leave it. It's tiny:```
Package: beep
Version: 1.3-4
Priority: optional
Section: universe/sound
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Rhonda D'Vine <rhonda@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 59.4 kB
Depends: libc6 (>= 2.7), debconf (>= 0.5) | debconf-2.0
Homepage: http://johnath.com/beep/
Download-Size: 23.2 kB
APT-Manual-Installed: yes
APT-Sources: http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Description: advanced pc-speaker beeper

```

But if you insist,```
sudo apt-get purge beep
```should do it but look at what else will be removed by first running```
apt-get purge -s beep
```where "-s" causes a simulation to be run and doesn't need sudo.

---

