---
title: "it's true selecting application alsa first goes to pulseaudio ?"
date: 2024-03-25
forum: General Help
---

### Post by aug7744 on 2024-03-25
Thanks for reading my topic.
I only want select the sound backend path using better and less cpu processing.
I see some replies in internet about if selecting in application the alsa sound goes that path

Program > alsa wrapper > pulseaudio > alsa

it's true ? Always selecting ALSA goes directly to pulseaudio using an wrapper ? Really in Ubuntu has an ALSA wrapper ?

Hmmm ... what is the default sound system in Ubuntu ? pulseaudio ? How use directly alsa in any application ?

Have an nice week.

---

### Post by Holger_Gehrke on 2024-03-25
Pulseaudio is still around, but is already partially superseded by pipewire. These two give you the ability to have multiple programs produce sound at the same time - they are acting as mixers (among many other things they can do; ALSA is much lower level, it's concerned with actually making the sound hardware work at all; the sound driver in the kernel is part of ALSA ...). If a program can directly talk to ALSA, you can temporarily suspend PulseAudio using the 'pasuspender' command, e.g. 'pasuspender mednafen somegame.nes' would suspend pulse, run the mednafen emulator with a nes game, and reactivate pulse afterwards. Obviously mednafen would have to be configured to actually talk to ALSA ...

If you're not just playing sound but actually working with it, then you might want to take a look at Ubuntu Studio. That has a low latency tuned kernel and uses JACK instead of PulseAudio.

Holger

---

