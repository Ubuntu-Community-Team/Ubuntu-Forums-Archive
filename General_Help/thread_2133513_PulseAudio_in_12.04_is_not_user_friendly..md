---
title: "PulseAudio in 12.04 is not user friendly."
date: 2013-04-08
forum: General Help
---

### Post by ka9qlq on 2013-04-08
I just upgraded from Kubuntu 10.04 to 12.04 xfce desktop and this was the first time a distribution upgrade did not crash. Hats off to team Ubuntu. PulseAudio has me at wits end though. In 10.04 I uninstalled it and with alsamixer I could individually select headset (front plugs) audio levels speakers (back plugs) and Police scanner (line in plug) AND I could individually select to mute them. PulseAudio is all or nothing. This is an improvement?

---

### Post by ka9qlq on 2013-04-19
Anybody know if I can just dump PulseAudoi for ALSA?

---

### Post by mörgæs on 2013-04-19
I don't know, but in Lubuntu Pulseaudio is not installed by default. Might be worth trying, if you have some space left for an extra partition.

---

### Post by dabl on 2013-04-19
Have you installed pavucontrol, and played with the mute and "set as fall back" buttons?  I use pavucontrol daily to switch between the mic on a webcam and my headset, and also to record via line-in.  It is a bit quirky, (sometimes it won't activate line-in until there is actually a signal on the line) but I think some of that depends on the hardware.

---

### Post by 3rdalbum on 2013-04-19
You can do that in regular Ubuntu 12.04, so any limitations you're experiencing in this regard are due to the default XFCE software, not the Pulseaudio backend.

If you want to stick with XFCE you can install the "pavucontrol" program, which gives you a fairly simple way of setting the volumes of input and output channels, and more.

---

### Post by ka9qlq on 2013-04-19
[ATTACH=CONFIG]241537[/ATTACH]
In my pavucontro only has one mute icon that controls all five outputs. If I click the unlink icon then I can individually adjust just eat one, however they do not stay where I put them.

---

### Post by dabl on 2013-04-19
> **ka9qlq said:**
> [ATTACH=CONFIG]241537[/ATTACH]
In my pavucontro only has one mute icon that controls all five outputs.


Right -- because "Analog Output" is a single output source.

There's some possibly useful information [**[color=green]here[/color]**](http://ubuntuforums.org/showthread.php?t=1559056).

---

### Post by ka9qlq on 2013-04-24
A simple and elegant solution. I uninstalled PulseAudio, ALSA lets me mute or unmute what I want and adjust audio levels as I want.

---

