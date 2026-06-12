---
title: "teamspeak"
date: 2008-04-22
forum: General Help
---

### Post by Tyke91 on 2008-04-22
I've gotten teamspeak installed perfectly, and it works. but it seems to take control of my sound card completely, i can't play any music while im using it. which gets kind of annoying.

ive got an hda intel sound card.

---

### Post by mriedel on 2008-04-25
Assuming you're running hardy, just start ts with a pulse audio wrapper by running "padsp teamspeak".

If you're running an older version of ubuntu / alsa instead of pulse, your solution is "aoss teamspeak".

---

### Post by Zanshin on 2008-04-27
> **mriedel said:**
> Assuming you're running hardy, just start ts with a pulse audio wrapper by running "padsp teamspeak".



Does that mean I can't run if from the icon loaded under Applications/Internet where it was loaded by the Synaptic Package Manager?

---

### Post by mahousaru on 2008-04-27
> **Zanshin said:**
> Does that mean I can't run if from the icon loaded under Applications/Internet where it was loaded by the Synaptic Package Manager?

System, Preferences, Main Menu, Internet {on the left}, right click Team Speak and select properties and then you can edit the command.

---

### Post by Zanshin on 2008-04-28
> **mahousaru said:**
> System, Preferences, Main Menu, Internet {on the left}, right click Team Speak and select properties and then you can edit the command.

Thanks, good lesson I can use other places (and now have!).

However, the pulse audio wrapper on TS resulted in lots o background noise.  

I used another approach, basically with a second sound card beyond the onboard.  I have the intel onboard audio but also a plantronics (880?) headset with the mini plugs which can be used optionally in an included usb dsp card.  So I use the usb dsp card for teamspeak (change "other" settings to "/dev/dsp1" and use that in sounds/audio conf/sound capture "OSS", Sound playback "auto".  Mixer then set to Intel HDA alsa, Sound events and Music & Movies both set to STAC92xxx analog and piped out my line out port to external speaker.  Not integrated and elegant, but both work cleanly.

---

### Post by kavon89 on 2008-04-28
> **Tyke91 said:**
> I've gotten teamspeak installed perfectly, and it works. but it seems to take control of my sound card completely, i can't play any music while im using it. which gets kind of annoying.

ive got an hda intel sound card.

EDIT: I scrolled over mriedel's response... essentially what he said. ;D I use aoss and have a bit of crackling noise, I might try the pulseaudio wrapper since aoss worked fine in older versions of Ubuntu.

---

### Post by pogush on 2008-04-28
i've run the program with

```
padsp teamspeak
```

now finally i can hear others speaking , but when i try talking others get my voice doubled and with echo.. what should i do? 
thx

---

### Post by Balachmar on 2008-08-28
I am also having the same problem.
Does someone have an answer to this question?
On how to fix the echo from mic when using 
padsp teamspeak

---

### Post by Cadeyrn on 2009-06-24
I alsa have that problem. Going down the list of sound servers:

-I had to uninstall all of OSS except for its mixer and the emulation of OSS offered by the other sound servers because it started blocking my sound card from being read by Ubuntu.
-ALSA works, but aoss teamspeak lets no other apps use sound, or has no sound if other apps are open. Plus the sound is crackly and hard to hear.
-ESounD works, but esddsp -m teamspeak lets no other apps use sound, or has no sound if other apps are open.
-PulseAudio would be completely perfect, except unlike all other PulseAudio voice capturing apps, my voice through padsp teamspeak has been echoing and in bad quality. My friends can barely hear what I'm saying.

I guess this has something to do with the bad programming of Linux-native TeamSpeak 2 because the guy who made it seems to be reluctant and quicker to remove unworking features than fix them, and/or a glitch with PulseAudio and uploading sound, and/or a glitch with PulseAudio emulating OSS. I should look for another app that captures the voice through OSS and use it through padsp. If the voice is echoing, then we know PulseAudio's OSS emulation needs to be improved before our problem is fixed.

EDIT: Erm... The only other program I can find that supports using OSS and captures the microphone's recording is Audacity, and Audacity won't let me record through OSS because it knows I removed OSS. I'll need someone else to perform this test for me...

---

### Post by Cadeyrn on 2009-06-24
Double-post, sorry.

---

### Post by Dante123 on 2009-08-03
I have found under 8.10 and 9.04 that to get Teamspeak to work under Ubuntu I have to do the following:

1. Make sure mic is working with sound recorder first (my default setup needed tweaking and front mic boost, some switches enabled for my system setup)

2. Install Teamspeak through add/remove programs.

3. Setup the teamspeak launcher on the desktop and edit it so that is runs "padsp teamspeak".

4. Kill Pulseaudio under System Monitor--->Preferences (I know this seems counter-intuitive since in step 3 we just told it to use padsp wrapper and then we kill pulseaudio in this step- but without doing this, there are choppy mic issues)

5. Run teamspeak from launcher on desktop and all should be well. Worked on my system anyway.

Hope this helps someone. If is works for you please reply.

Take care!

---

