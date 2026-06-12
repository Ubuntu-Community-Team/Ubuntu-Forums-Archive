---
title: "Chrubuntu 14.04 Audio problem"
date: 2014-05-26
forum: General Help
---

### Post by hisham2 on 2014-05-26
Hi guys,
I have a Samsung Series 3 Chromebook (ARM Processor), I was able to install Ubuntu 14,04 with dual boot, I'm very pleased with this new version (as I had on it 12,04 before i had some issues with the touch pad, runs a bit slow, crashed too often, and i was never able to boot to chrome OS), my only issue is there is no sound, i tried a handful of ideas but no luck, does anyone know how to solve this issue? Thank you,
FYI I am using Xfce

---

### Post by christopher15 on 2014-07-30
I am also experiencing the same problem, I was hoping someone had an update or a suggestion to try

---

### Post by ingegnue on 2015-01-05
I am also trying to sort out the sound for this model. So far I've tried the method that worked for other chromebooks, but no luck for me. The method, detailed in this blog and repeated in others: [http://retrofatty.blogspot.nl/2013/02/chrubuntu-install-and-fixes.html](http://retrofatty.blogspot.nl/2013/02/chrubuntu-install-and-fixes.html)

> 
[B]YOU MUST FOLLOW THIS EXACTLY OTHERWISE YOU COULD
[B]DAMAGE YOUR SPEAKERS.

Open a new terminal window "CTRL+ALT+T" and type "alsamixer" (without quotation marks) and then hit "Enter".
You will get the AlsaMixer v1.0.25 mixer screen.
At the bottom of the window you will see Headphone and Speaker options, notice that Headphone is in red with indicates that it is the item selected.
Navigate through this program using your arrow keys (Do not use scroll on your mouse as this will alter the levels which you do not want to do).

Start by pressing the right arrow until "Left Speaker Mixer Left DAC1" is selected in red.
List is alphabetical so you will know when it is coming up, but if you do miss it just hit the left arrow to go back.
You will notice that the box above contains the letters MM this means that the channel is muted.
This is what we need to change.  Press the "M" key and the MM should change to 00
You have successfully enabled the channel.  Do the same thing with the following channels:
"Left Speaker Mixer Right DAC1"
"Right Speaker Mixer Left DAC1"
"Right Speaker Mixer Right DAC1"
Now we will enabled the headphone output, same process enable the following:
"Left Headphone Mixer Left DAC1"
"Left Headphone Mixer Right DAC1"
"Right Headphone Mixer Left DAC1"
"Right Headphone Mixer Right DAC1"

Now press "Esc" and you should be back at the terminal screen.
At this point we have all of the settings in place but we have to save otherwise Ubuntu will forget next time we reboot and we will have to enter all of this again. Type the following command:

[B]sudo alsactl store

You will be prompted for your password so just enter that and your settings will be stored.
Exit terminal.
Now go to the speaker icon on the top right of your screen (next to the clock) left click and go to "Sound Settings".  Underneath where it says "Play sound through" select "Speakers" and test the sound using the volume slider.[/B][/B][/B]

I think the problem is that it worked for everyone using the GNOME or Unity DEs but I'm using xfce. Either that, or it's that the method is outdated perhaps. I just have "dummy" speakers; the real ones aren't detected.

---

### Post by ingegnue on 2015-01-05
[http://www.tomshardware.co.uk/answers/id-2277455/dual-booting-chromebook-xubuntu-audio.html](http://www.tomshardware.co.uk/answers/id-2277455/dual-booting-chromebook-xubuntu-audio.html)

This looked promising, but no luck for me. pacmd list-sinks lists only ONE sink - the dummy speakers.

I hope someone else finds it useful anyway. I've given up after wasting a day on this.

---

