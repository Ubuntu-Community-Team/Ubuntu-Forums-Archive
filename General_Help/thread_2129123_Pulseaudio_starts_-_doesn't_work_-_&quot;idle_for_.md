---
title: "Pulseaudio starts - doesn't work - &quot;idle for too long, suspending&quot;"
date: 2013-03-25
forum: General Help
---

### Post by J V on 2013-03-25
I installed pulseaudio-dev trying to troubleshoot what turned out to be a miscompiled libav - and now pulseaudio won't start. It shows no errors or warnings - all I know is that the indicator still shows no difference and I have no audio.

Running pulseaudio from terminal gives me:

```
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
```

There's nothing in syslog or dmesg that give any hints.

I've tried reinstalling pulseaudio (And all the packages that were dependant on it) but no luck so far.

It's possible it's hanging in initiation because there's no difference between a working pulseaudio command and one that hangs.

Edit: Yay I found out how to get log info from pulse:

```
I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.usb-046d_0802_F1851F50-02-U0x46d0x802.analog-mono idle for too long, suspending ...
I: [alsa-source] alsa-source.c: Device suspended...
I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
I: [alsa-source] alsa-source.c: Device suspended...
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
I: [alsa-sink] alsa-sink.c: Device suspended...
```

Right. Now what?

Embarrasing edit: fuser /dev/snd/* shows pulseaudio connected to devices... Hmm... What if I... MUTED? I just spent 2 hours finding the MUTE BUTTON? /facedesk

---

