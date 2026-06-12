---
title: "Youtube video no sound in Firefox[Solved]"
date: 2006-12-18
forum: General Help
---

### Post by alimovz on 2006-12-18
Hey guys. I can play video on youtube on my firefox but get no sound. :-(
I am using Ubuntu 6.0

Thanks for any help

---

### Post by divague on 2006-12-18
Try this

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

restart firefox.

---

### Post by zmuth734 on 2007-01-05
> **divague said:**
> Try this

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

restart firefox.

Thanks that works.

---

### Post by bionnaki on 2007-01-05
I *highly* recommend updating to the flash betas. search the forums and you'll find out how.

---

### Post by MeanStreak on 2007-11-20
> **divague said:**
> Try this

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

restart firefox.

Does this fix also apply for Ubuntu Gutsy Gibbon? 

I followed the directions (quoted above) but still have no sound for YouTube videos. I'm a semi-noob - could someone clarify how to change the FIREFOX_DSP settings (I edited the file and then saved, then restarted Firefox - I presume that is how it is done?) 

Note: My sound device is an M-Audio FastTrack Pro. Sound is working perfectly when playing MP3s with my audio player.

---

### Post by MeanStreak on 2007-11-26
Just a follow up - I disconnected the Fast Track Pro, rebooted and sound in YouTube is now working via my on board sound card. Can only presume there was an issue with the Fast Track Pro.

---

### Post by Squizz on 2007-12-08
> **divague said:**
> Try this

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

restart firefox.

This also worked for me on a clean install of Gutsy 7.10 along with installing Gnash.

The controls are a bit squashed up, but I have picture and sound on **most** of the flash based videos I've tried.

---

### Post by mikey-sd on 2008-02-03
The solution that worked for me.  Maybe it will help someone else too.

I had Gnash and Flash installed, and once I removed Gnash, the sound worked.  Using Gutsy 7.10.  I removed Gnash the Noob way using Synaptic Manager.

Have a look by typing about:plugins in your firefox browser.

Peace.

---

