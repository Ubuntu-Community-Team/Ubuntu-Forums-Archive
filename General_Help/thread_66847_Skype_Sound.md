---
title: "Skype Sound"
date: 2005-09-18
forum: General Help
---

### Post by Tylo on 2005-09-18
Has anyone been able to successfully allow both Skype and any music player to both output sounds through their speakers at the same time?

For example:

Someone calls you on Skype, but you're playing music. Does Skype ring?

---

### Post by Tylo on 2005-09-18
I don't know what the rules are for bumping in this place, but I'm sorry guys, I really really would love to figure this out. Please help me if you can.  :|

---

### Post by Drakx on 2005-09-19
[QUOTE=Tylo]Has anyone been able to successfully allow both Skype and any music player to both output sounds through their speakers at the same time?

For example:

Someone calls you on Skype, but you're playing music. Does Skype ring?[/QUOTE]
 Yes :)

Im guessing your using on board sound right ? if so forget it will not happen with AC97 cards your best bet is to get a sound blast live with emuk101 chip set then you should find that you will not have any sound issues again :)

---

### Post by angkor on 2005-09-19
[QUOTE=Drakx]Yes :)

Im guessing your using on board sound right ? if so forget it will not happen with AC97 cards your best bet is to get a sound blast live with emuk101 chip set then you should find that you will not have any sound issues again :)[/QUOTE]

*blinks*

I have an onboard ac97 soundcard and I *do* have full duplex sound. So it is definately possible. I'm sorry I do not quite remember what I did to get this working but it had something to do with configuring alsa correctly.

---

### Post by Tylo on 2005-09-19
Angkor: could you post your asound.conf file?


And, if you have it, your .asoundsrc?

And, could you tell me if you have ALSA configured to be both your default Sink and default Source?

[img]http://students.cup.edu/coo9893/pics/MSS.png[/img]

---

### Post by greyhound4334 on 2005-09-26
I'm far from an expert on this stuff, but I do have my sound working the way you asked.  Note that I use KDE -- so if you use gnome, you need to adapt slightly (there's a gnome equivalent to artsdsp).  I assume you have skype working "on its own", but need to know how to make it work alongside, say, amarok.

My onboard sound (nvidia Realtek ALC850) doesn't appear to have hardware mixing, so I need to use the aRts sound daemon (esd if you're using gnome).  You need to make sure aRts is configured correctly -- a couple of quick things to make sure of: full duplex should be checked on the hardware tab; don't make your sound buffer too large (I have mine set to 92ms); I have autosuspend set for 5 secs (I don't think that matters here, but this is part witchcraft, so I'm not 100% sure what *does* matter)).

The key ingredient seems to be to run skype with artsdsp, as in "artsdsp -m skype" from the command line (or as the command line in a desktop/menu icon).  As far as I understand it, this launches skype in a manner that it talks to artsd instead of taking over your sound card directly.  I believe launching skype directly causes it to take exclusive control of your (non-hardware-mix) soundcard because skype is an oss application.  Thus it won't play nicely with other apps that want to access the sound card.  artsdsp solves this problem nicely.

I'm now able to listen to music, and still hear my skype phone ring.  I can turn down the volume of the music, or mute it entirely, while on a phone call, then resume it when the call is over.  I can make multiple phone calls in skype without having to restart it.  All in all, it seems to be working pretty well.

HTH,
john

---

### Post by gsuveg on 2005-11-15
with artsdsp -m skype the skype drop me a segment failure, and core dump.  :confused: 

its a breezy and kde. any more idea ?

---

