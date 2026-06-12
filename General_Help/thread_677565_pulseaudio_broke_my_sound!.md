---
title: "pulseaudio broke my sound!"
date: 2008-01-24
forum: General Help
---

### Post by insert_name_here on 2008-01-24
I'm running a fully updated Gutsy on a Lenovo Thinkpad t60 with intel integrated audio.

So I installed pulseaudio, right, because I'd like to be able to mix sound from different programs on my computer. (No streaming, far too complicated for me :D )  

I installed just about everything with pulseaudio in the name in synaptic and changed by .asoundrc file.  I added my username and 'root' to the groups 'pulse', 'pulse-rt' and 'pulse-access'.  

However, I can't play sound in most programs.  It works fine in VLC, but amarok (which I switched to use pulseaudio as its output engine) and totem don't work.  (Amarok complains about xine being busy, and totem just doesn't work)

Help?

---

### Post by insert_name_here on 2008-01-25
pulseaudio doesn't start up.  When I try to start it, either as my user or as root, I get the following errors.

```
 pulseaudio
E: module-alsa-sink.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0 sink_name=alsa_output.pci_8086_27d8_alsa_playback_0"): initialization failed.
E: authkey.c: failed to open cookie file '/home/merrillj/.pulse-cookie': Permission denied
E: authkey.c: Failed to load authorization key '/home/merrillj/.pulse-cookie': Permission denied
E: module.c: Failed to load  module "module-native-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

```

---

### Post by insert_name_here on 2008-01-29
bumpity-bumpity-boo.'

Any ideas?

---

