---
title: "Sound Not Working"
date: 2008-07-05
forum: General Help
---

### Post by nickhk on 2008-07-05
Just installed Ubuntu for the first time. Installation was smooth, but sound doesn't work. It was working when I was using Windows XP, just prior to installing Ubuntu - so I don't think its a hardware problem. Driver perhaps? 

Any ideas?

---

### Post by scragar on 2008-07-05
I've seen this many times before, first thing I would check(personaly since it's always been the problem with my sound card) is the default sound card. install **asoundconf-gtk** via the package manager(System>applications>Synaptic) or a terminal(Applications>accessories>Terminal ```
sudo apt-get install asoundconf-gtk 
```)
and run it(System>Prefernces > default sound card) just check the sound card is selected, close and test.

---

### Post by nickhk on 2008-07-05
Thanks for the quick feedback! I tried your suggestion, but still nothing. 

I am using an HP Pavilion that is about 4 or 5 years old. I remember changing a sound card on one of my machines a few years ago, but can't remember if it was this one or not.

---

### Post by scragar on 2008-07-05
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

there's a guide there, it doesn't help everyone though.

---

### Post by nikgare on 2008-07-05
Do you have more than one soundcard?
If so, go to Sytem->Preferences->Sound and select the right output.

If not, have you checked in the Volume Control Dialogue that the right sliders are high enough and the outputs are turned on?

---

