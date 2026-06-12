---
title: "How TO: Getting Microphone to work"
date: 2006-12-04
forum: General Help
---

### Post by subiet on 2006-12-04
Ok if you suffer from that "i can hear my mic thru the speaker, but can't get skype/ekiga/sound recorder to hear me" problem this might help

1) Use ALSA only, it is good and it works(all those tips telling you to use OSS, for some reason didn't work for me, or for a few friends of mine)

(you can choose this via system>pref>multimedia selector


2) type in alsamixer at terminal, toggle via "tab key" to "capture" view, there you will see a row, with "capture" written on the bottom, increase the volume to that to maximum. (increase the vol to maximum, for any row you can,in this window)

3)open sound recorder, and in the option, where it says, "record from", chose "capture".

4) test it and it should work, just in case it doesn't, and you had increase the volume from zero to maximum of any other row also in the alsamixer, try putting that too.

5)to kill the annoying feedback, you can always mute the mic permanently, and choose the capture from mic option in the volume control.

---

### Post by midtoad on 2006-12-04
I didn't have any success with this how-to UNTIL I tried the Mic-boost +20dB setting in the Sound Recorder Edit Preferences. then I could hear myself!

---

### Post by IamAcoconut on 2007-01-11
Tried this and also enabled Mic Boost. No luck.
I it is a tiny bit louder than before, yet Skype doesn't hear me at all, while it previously had.

---

### Post by Souljah on 2007-01-18
I have tried all these settings to no avail myself. I don't know why it doesn't work. :(

---

### Post by subiet on 2007-01-18
maybe some problem with your hardware

---

### Post by Sparky222B on 2007-08-01
Yes! Works! Finally! Thanks!

---

### Post by Raistlin355 on 2007-10-21
Worked perfect first time!!  Now i just have to work out the humming noise, and ideas on that?  I'm figuring its the lappy cause I had the same problem with Winder$

---

### Post by TearDownAllSigns on 2007-12-02
Thank you very much for all of this, ALSAMixer is much better than messing with adding things in the volume control. When I turned everything up and put on the Mic boost I could record audio at a good volume. 

However Skype was still really quiet, until I figured out that it was almost completely muting my Mic every time I made a call. If you go to Options -> Sound Devices in and uncheck "Allow Skype to automatically adjust my mixer levels" it should take care of that. Now it works great.....for the mic. I still need to figure out how to get Skype to send phone sound to just the rear channel that the headset is plugged into on my Audigy 2.

This goes down as one of those usually easy things that are way too obscure in Ubuntu. Having to manually edit an xorg.conf just to get my 5 button mouse to work also comes to mind.

---

### Post by marn on 2007-12-17
Thankyou for the HowTo - worked for me. I don't understand why a seemingly necessary option isn't included in the volume settings in the task bar though.

---

### Post by zidkenu on 2008-06-22
Guys, there are too many issues with microphone capture volume: sound card driver, impedance, analog noise, volume gain+pre amp... do yourselves a favor, google "ubuntu USB Microphone Logitech/Plantronics/Rocketfish",  just reset sound capture source in alsamixer... Easy!

---

