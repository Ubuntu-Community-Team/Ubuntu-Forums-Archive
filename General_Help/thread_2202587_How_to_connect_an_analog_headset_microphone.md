---
title: "How to connect an analog headset microphone?"
date: 2014-01-29
forum: General Help
---

### Post by john_ladasky on 2014-01-29
Hi folks,

I'm running Ubuntu 13.10 (64-bit, on an AMD 1100T desktop CPU, if any of that matters).  My son has been having trouble with his gaming headset over on his Windoze system.  It worked for a while.  The speakers are still working.  He says the microphone has stopper working.  I'm not convinced that it isn't a software issue.  So, I want to test the headset on my system.

The headset is a Razer Kraken.  I'm sure that the make and model are unimportant.  What is important is that it's an analog headset.  It has a four-lead wire coming out of it.  It came with an analog splitter, so that you can plug it into the 1/8" audio jacks on the computer.

I have it plugged into my machine right now.  From System Settings > Sound, I can send audio to the headset speakers by selecting the Built-in Audio/Analog Output device under the Output tab.  So far, so good.  However, when I click on the Input tab, my only choice is a Digital S/PDIF input.

How do I add an analog output to this menu?  Thanks for any advice you may have.

---

### Post by Bucky Ball on 2014-01-29
Open a terminal and type in:

alsamixer

See if anything is muted or switched off/muted in there. Hit F6 and see if you can find any other sound cards that might be muted.

---

### Post by john_ladasky on 2014-01-30
Thanks, Bucky Ball.

In alsamixer, I observed that I have coarse and fine microphone gain settings, just as I recall from my son's Windows setup.  It appears that I have separate controls for the front mic jack and the rear.  I'm interested in the front jack.

Both the coarse and fine gains were set as low as they could go -- essentially, muted.  The coarse gain ranges from 0 dB to +30 dB in 10 dB increments.  The fine gain ranges from -34.5 dB to +12 dB in 1.5 dB increments.

Now, when I turn these gain settings up, what do I do next?  I'm not seeing any changes in my System Settings window when I change the gains (not that I expected to).  I want to test the microphone.  I would either like to see a volume meter jump when I talk into it, or hear some sound come out of my speakers and/or headset.

---

### Post by Bucky Ball on 2014-01-30
I think you have Pulseaudio Volume Control installed by default (I don't use Ubuntu so don't know). If not, install with:

sudo apt-get install pauvcontrol

It will then be found in the Multimedia apps. Launch it. Get some sound going (make a Skype test call or some other app that involves the mic), click the 'Recording' tab and see what device it is using. When you click on the device for the audio stream you should get a selection of available devices.

---

### Post by tgalati4 on 2014-01-30
The preamplifiers on the motherboard are probably shot.  Static electricity and plugging-unplugging can cause high voltage damage.  Most microphones are plug and play.  If you turn up the gains and don't hear anything or see any action on the meters then you can be pretty sure the preamps are shot.  Get a USB sound stick and use that as the input or get a cheap sound card.

I have seen this on other systems.  First the sound chip goes.  Next USB ports mysteriously disappear, then graphics go strange.  These are signs of motherboard failure.  Check the capacitors and the voltages in BIOS or with a meter.

---

