---
title: "[SOLVED] Flaky Sound with Wine"
date: 2008-06-13
forum: General Help
---

### Post by azurepancake on 2008-06-13
I've recently got my video card working well with Ubuntu (ATI Radeon x1600) and I've been able to get a decent chunk of my video game library to work with Wine. Games like World of Warcraft, Starcraft and the Steam suite.

Everything works great besides one issue. Sometimes the audio works and sometimes it does not. It's quite odd. It seems if I really want sound to function in a game, I need to keep rebooting Ubuntu until it works. I have no idea why its doing this!

I have a Audigy 2 ZS and I've configured PulseAudio following this guide, [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739).

In the audio tab in Wine configuration, I have the OSS driver selected (because I am told this works better with World of Warcraft). I also set hardware acceleration to "Emulation".

That is all I changed. By default, the sample rate is 44100 with a bits per sample of 16.

Also, when I type "winecfg" into terminal I get the following output..

```

fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.

```

I have tried the ALSA drivers and still have the audio problem. When I load "winecfg" from terminal while ALSA drivers are activated, I get the following output..

```

fixme:mixer:ALSA_MixerInit No master control found on USB Uno MIDI Interface, disabling mixer
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.

```

I'm quite clueless! If anyone has any advice I'd greatly appreciate any kind of input. If you need anymore information, just ask.

Thanks.

---

### Post by joshsmith on 2008-06-13
install and run the program pavucontrol, this shows active streams as seen by pulseaudio

if wine doesnt appear in pavucontrol, then it wont make sound it some other app is there (as it will hog the sound card). maybe this is what you are experiencing

to get wine to go through pavucontrol, best bet is to use oss sound in winecfg and start the app as
padsp wine path/to/app.exe

---

### Post by azurepancake on 2008-06-13
That did the trick! I guess I missed that little bit at the end of that guide. 

Thank you very much!

---

