---
title: "Weird issue with sound"
date: 2018-12-06
forum: General Help
---

### Post by olivar on 2018-12-06
Hello,

Let me preface this by saying I'm really new when it comes to Ubuntu.
My experience is rather limited, and I think I've gotten into some mess now where I might have accidentally broken the sound system.
To give some background information:

I have a Razer Blade 15 laptop from 2018, few weeks old really.
Because of the development I do, I decided to install Ubuntu and Cinnamon on it as my preferred setup.
Everything pretty much works fine, until I received my new headset today.
It didn't get recognized so I started googling and playing with settings, changing installation packages and what not.
The current situation is that I removed & reinstalled pulseaudio, and now I have some problems:


[LIST]
[*]The audio options are visible on my desktop
[*]On boot, I get the drum sound when prompted to enter my password
[*]One I am on the desktop however, I don't get any sound:
[LIST]
[*]Using the test speakers option, no sound plays
[*]using the aplay command however I do get sound when loading the FrontLeft.wav file
[*]Headset doesn't work at all
[/LIST]
[/LIST]

Some basic information about my system:

&#10140;  ~ aplay -l  
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

&#10140;  ~ lspci -v | grep -A7 -i "audio"                                        
00:1f.3 Audio device: Intel Corporation Device a348 (rev 10)
    Subsystem: Razer USA Ltd. Device 2001
    Flags: bus master, fast devsel, latency 32, IRQ 164
    Memory at ad410000 (64-bit, non-prefetchable) [size=16K]
    Memory at ad100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


I was able to get sound working before all this when I control all volume settings manually using alsamixer and pavisoundcontrol from the command line.
Would someone be able to help me fix this?

---

### Post by olivar on 2018-12-06
I somehow managed to get at least notification sounds from discord etc working.
But Slack and Skype still don't produce sound or pretty much anything else.

I'm also open for pointers on helping me debug this.

---

### Post by CatKiller on 2018-12-06
So it sounds like the system is picking up the hardware and setting the default OK automatically (because you have sound at the login screen) . It's just that through your playing, you've configured your user account to use something different (because you don't have sound when logged in).

You could either use something like pavucontrol and paman in combination with the volume control widget to set the defaults how you want them, or nuke the per-user configuration files in your Home folder to let it auto-configure again.

---

### Post by olivar on 2018-12-06
> **CatKiller said:**
> So it sounds like the system is picking up the hardware and setting the default OK automatically (because you have sound at the login screen) . It's just that through your playing, you've configured your user account to use something different (because you don't have sound when logged in).

You could either use something like pavucontrol and paman in combination with the volume control widget to set the defaults how you want them, or nuke the per-user configuration files in your Home folder to let it auto-configure again.

How would I go about to auto-configure this?
I've for example deleted all the files I found in a similar thread in my home folder related to pulse etc.
And ran the pulseaudio -vvvvv command which dumps a lot of output, but seems to hang now and then on certain steps.

I could try playing again with the pavucontrol and paman settings and see if I can find some combination that works.
Just to be clear, these  should be used without sudo or anything right?

---

### Post by CatKiller on 2018-12-06
PulseAudio and ALSA may both have files in your Home folder. ALSA handles the hardware side of things and PulseAudio handles the signal routing part of things, generally. 

> **olivar said:**
> Just to be clear, these  should be used without sudo or anything right?
That's right. Running them with sudo could well give you other problems.

It is possible that the headset won't work at all: I'm posting from my phone, so I'm not going to look up whether it's supported or not. We should be able to get everything else working again, though.

---

### Post by olivar on 2018-12-06
I've cleared all folders, and when I got home, I booted up the laptop and could play stuff normally.
So sound from Firefox etc and the music player seemed to be working properly through the speakers
That's definitely progress.

I still notice one thing:
When opening the sound settings, and pressing the "Test Sound" button, I can click the left and right speakers, but no sound plays.
So something in this applet still seems to be wrong.

Will try tomorrow at work whether the headset works properly or not.

---

### Post by olivar on 2018-12-07
Okay, so an update:


[LIST]
[*]Using alsamixer I am able to direct sound through the headset now
[*]I need to manually use alsamixer every time I plug in/out the headset
[*]Microphone on the headset doesn't seem to be recognized by the OS/Alsa at all.
[*]Headset is a Logitech prodigy G231
[*]OS doesn't see the headset being plugged in/out
[*]Using the Sound configuration from the settings still doesn't seem to work outside the volume slider
[/LIST]

So I think I'm at least back at the place I started after reinstalling/purging etc.
Would be cool if I could get the system to recognize when the audiojack is used so it adjust volume accordingly, e.g like in Windows or OSX

---

### Post by CatKiller on 2018-12-07
A couple of things to check:

The cable has an inline mute switch. Have you tried it in both positions?

Are you using two sockets for the headphones and microphone using the Y-splitter, or a single combined socket? If you're using a combined socket, does it have the same configuration as the headset?

It's a shame you've not managed to get the panel applet to behave again; it is a very convenient place for configuration. The system should be able to sense when something's plugged in, if it's supported by the hardware, and switch accordingly. I don't know that it remembers different volume levels.

---

### Post by olivar on 2018-12-07
Hey CatKiller,

first of all, thanks for all the help so far.
I checked with both the switch on and off, but from what I can tell it doesn't seem to be making much difference.
I'm using a single pin that combines all into one. It's part of the headset. I can't use a Y splitter as there's only one bus to connect on unfortunately.

I can live with the applet for now, but do you know where this applet might store configuration etc?
Perhaps something needs to be double checked there as well.

---

### Post by CatKiller on 2018-12-07
While mono and stereo plugs are standardised in their spacings, the combined ones aren't. It's *probably* the same for the headset and laptop, but there is a chance that it isn't.

I'm not sure where Cinnamon stores its settings. In Gnome it would have been a gconf/dconf setting, so Cinnamon might have picked that up, or it might do something different. If it's not using dconf, ~/.local would be a reasonable place for them to have put it.

---

