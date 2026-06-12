---
title: "Wrong soundcard in Media Players"
date: 2005-04-19
forum: General Help
---

### Post by Retain on 2005-04-19
Ok, now go easy on me as I'm a Linux n00b. Installed Ubuntu this morning and most things are going well. I've done a lot of reading and learning as I've been going and so far I'm loving it! Here's the problem though:

I have two soundcards in my system, the onboard RealTek chip and a MuseXL something (I can't remember the exact model but it's not important anyway). Both cards are detected and in fact work fine. Here's the weird part. All my 'desktop' sounds (logging in, button clicking, logging out, etc) all come through the onboard chip. This is good, as I only want to use the onboard at the moment. However, everything I play through media players (tried Totem and VLC) comes out of the other card. Both video files and audio files have the same symptom. Disabling and/or removing the card isn't an option as it will eventually be used with my VoIP software (as it was in Windows). I've done a bit of digging but can't really find anything to help.

Any ideas? TIA

---

### Post by eXidos on 2005-04-19
Perhaps check the setting in your audio and video player to see if the output device can be configured.

---

### Post by Retain on 2005-04-19
I have and while there are configuration options, there's nothing to select which card to use. I'm thinking it has to be some sort of system settings for it to affect all media players. Sadly, my Linux experience can be counted in hours so I'm stuggling to find out what it is!!

---

### Post by Retain on 2005-04-19
Aaaarghh!! This is doing my nut in!! Ok, so I noticed I didn't have sound in Flash, so did the following to fix it:

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

Now, all my music and videos play their sound through the correct (onboard) sound card for 2 seconds, then it cuts back to the other one. What's going on?!

---

### Post by kleeman on 2005-04-19
Here's a wiki on how to deal with multiple cards and force one in particular to be chosen. It's a bit confusing but has plenty of ideas to try:

[http://alsa.opensrc.org/index.php?page=MultipleCards](http://alsa.opensrc.org/index.php?page=MultipleCards)

---

