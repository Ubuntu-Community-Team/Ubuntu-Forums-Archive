---
title: "Pulse Audio -- Missing Sink"
date: 2008-01-07
forum: General Help
---

### Post by ~LoKe on 2008-01-07
Well, I've finally managed to get Pulse Audio working (and by working, I mean loosely).  The problem I'm having is that in the list of "sinks", my onboard audio device isn't listen.  It only has my soundcard, which isn't what I want.  How would I go about making it detect my onboard sound?

---

### Post by rubicon on 2008-01-07
Well, I'll try my best to help you. Lets' begin with posting your sinks.
```
pactl list
```
and 
```
cat /etc/pulse/default.pa
```

---

### Post by ~LoKe on 2008-01-07
Thanks for showing up!  Fortunately, the sinks have shown up after a reboot.  **Un**fortunately, I get no sound though my main device.  Everything will play (albeit, poorly) through my soundcard (which I have my headset plugged into), but not through my onboard sound.  Both sinks are listed in padev, and I've selected them both.  But here's the info you asked for:

**pactl list** (the **bolded** blocks are my onboard sound, the device I'd like to use)
> *** Module #0 ***
Name: module-alsa-sink
Argument: device_id=1 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0
Usage counter: n/a
Auto unload: no

*** Module #1 ***
Name: module-alsa-source
Argument: device_id=1 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0
Usage counter: n/a
Auto unload: no

[b]*** Module #2 ***
Name: module-alsa-sink
Argument: device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
Usage counter: n/a
Auto unload: no

*** Module #3 ***
Name: module-alsa-source
Argument: device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0
Usage counter: n/a
Auto unload: no[/b]

*** Module #4 ***
Name: module-hal-detect
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #5 ***
Name: module-esound-protocol-unix
Argument: socket=/tmp/.esd/socket
Usage counter: n/a
Auto unload: no

*** Module #6 ***
Name: module-native-protocol-unix
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #7 ***
Name: module-volume-restore
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #8 ***
Name: module-default-device-restore
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #9 ***
Name: module-rescue-streams
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #10 ***
Name: module-suspend-on-idle
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #11 ***
Name: module-x11-publish
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Module #12 ***
Name: module-native-protocol-tcp
Argument: auth-anonymous=1
Usage counter: n/a
Auto unload: no

*** Module #13 ***
Name: module-esound-protocol-tcp
Argument: auth-anonymous=1
Usage counter: n/a
Auto unload: no

*** Module #14 ***
Name: module-zeroconf-publish
Argument: 
Usage counter: n/a
Auto unload: no

*** Module #15 ***
Name: module-zeroconf-discover
Argument: 
Usage counter: n/a
Auto unload: no

*** Module #16 ***
Name: module-gconf
Argument: (null)
Usage counter: n/a
Auto unload: no

*** Sink #0 ***
Name: alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0
Driver: modules/module-alsa-sink.c
Description: ALSA PCM on front:1 (C-Media PCI DAC/ADC) via DMA
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Owner Module: 0
Volume: 0: 100% 1: 100%
Monitor Source: 0
Latency: 0 usec
Flags: HW_VOLUME_CTRL LATENCY HARDWARE

[b]*** Sink #1 ***
Name: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
Driver: modules/module-alsa-sink.c
Description: ALSA PCM on front:0 (ALC883 Analog) via DMA
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Owner Module: 2
Volume: 0: 100% 1: 100%
Monitor Source: 2
Latency: 0 usec
Flags: HW_VOLUME_CTRL LATENCY HARDWARE[/b]

*** Source #0 ***
Name: alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor
Driver: modules/module-alsa-sink.c
Description: Monitor Source of ALSA PCM on front:1 (C-Media PCI DAC/ADC) via DMA
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Owner Module: 0
Volume: 0: 100% 1: 100%
Monitor of Sink: 0
Latency: 0 usec
Flags: 

*** Source #1 ***
Name: alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0
Driver: modules/module-alsa-source.c
Description: ALSA PCM on front:1 (C-Media PCI DAC/ADC) via DMA
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Owner Module: 1
Volume: muted
Monitor of Sink: no
Latency: 0 usec
Flags: HW_VOLUME_CTRL LATENCY HARDWARE

[b]*** Source #2 ***
Name: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0.monitor
Driver: modules/module-alsa-sink.c
Description: Monitor Source of ALSA PCM on front:0 (ALC883 Analog) via DMA
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Owner Module: 2
Volume: 0: 100% 1: 100%
Monitor of Sink: 1
Latency: 0 usec
Flags: [/b]

*** Source #3 ***
[b]Name: alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0
Driver: modules/module-alsa-source.c
Description: ALSA PCM on front:0 (ALC883 Analog) via DMA
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Owner Module: 3
Volume: 0: 100% 1: 100%
Monitor of Sink: no
Latency: 0 usec
Flags: HW_VOLUME_CTRL LATENCY HARDWARE[/b]

*** Client #0 ***
Name: PulseAudio Manager
Driver: pulsecore/protocol-native.c
Owner Module: 6

*** Client #3 ***
Name: pactl
Driver: pulsecore/protocol-native.c
Owner Module: 6

*** Sample #0 ***
Name: pulse-hotplug
Volume: 0: 100% 1: 100%
Sample Specification: s16le 2ch 44100Hz
Channel Map: front-left,front-right
Duration: 0.0s
Size: 0 B
Lazy: yes
Filename: /usr/share/sounds/startup3.wav

**cat /etc/pulse/default.pa**
> #!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink

#load-module module-alsa-sink device=hw:1
#load-module module-alsa-source device=hw:1
#load-module module-alsa-sink device=hw:0
#load-module module-alsa-source device=hw:0

#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists /usr/lib/pulse-0.9/modules//module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Load several protocols
load-module module-esound-protocol-unix socket=/tmp/.esd/socket
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Publish connection data in the X11 root window
.ifexists /usr/lib/pulse-0.9/modules//module-x11-publish.so
load-module module-x11-publish
.endif

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists /usr/lib/pulse-0.9/modules//module-gconf.so
load-module module-gconf
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
#load-module module-native-protocol-tcp listen=0.0.0.0
#load-module module-waveout

And, just in case:
**~/.asoundrc**
> pcm.pulse { type pulse }

ctl.pulse { type pulse }

pcm.!default { type pulse }

ctl.!default { type pulse }

It worked earlier, but I have NO idea what I changed.  Perhaps I modified my .asoundrc...I'm lost.

---

### Post by rubicon on 2008-01-07
If you have had sound through your on-board card before, then it is probably problem in device detecting, afaict.

Try to manually load audio-drivers. To do it, look closer at this section in default.pa:
```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink

#load-module module-alsa-sink device=hw:1
#load-module module-alsa-source device=hw:1
#load-module module-alsa-sink device=hw:0
#load-module module-alsa-source device=hw:0

#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

```I think you could try to specify these options for modules:
```
load-module module-alsa-sink device=hw:0
load-module module-alsa-sink device=hw:1

```

It seems that ALSA may alter the order in which your two audio-devices get recognized. The above two lines, I believe, will at least add both your sound-cards to available sinks. Try it and notice what'll happen. The best variant -- your both sound-cards will produce sound.

---

### Post by rubicon on 2008-01-07
Oh, and you may need to disable automatic detection of sinks, to do it, comment this part:
```

### Automatically load driver modules depending on the hardware available
.ifexists /usr/lib/pulse-0.9/modules//module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

```

---

### Post by rubicon on 2008-01-07
Um, wait. I have noticed something. You already have sinks from you on-board card currently! Try to play something using pacmd.

---

### Post by ~LoKe on 2008-01-07
Gave those a shot.  I still have both sources and sinks, and audio still plays through my headphones, but not my speakers.  The odd thing is is that it thinks it's playing, as in, the test playback doesn't fail, and it shows that something is trying to play through the proper sink, but there's just...no sound.  It's pretty strange.

---

### Post by ~LoKe on 2008-01-07
> **rubicon said:**
> Um, wait. I have noticed something. You already have sinks from you on-board card currently! Try to play something using pacmd.

How would I do that? :D

> >>> play-sample
You need to specify a sample name and a sink name.


---

### Post by rubicon on 2008-01-07
Sorry for another bunch of info, but I'm, like, on fire :)

To test my audio sinks, I run 'pacmd', enter 'help' (to view a list of commands), enter 'list-sinks', then 'play-file /usr/share/sounds/startup3.wav *name-of-a-sink or index*', that works. Then I run 'set-default-sink *name-of-a-sink or index*'. Sorry, I have only one sink, so it works always and I can't say where it may go wrong :)

---

### Post by ~LoKe on 2008-01-07
0 is onboard
1 is soundcard
```
play-file /usr/share/sounds/startup3.wav 0
```
Plays nothing.  Index 1 plays through my headphones.  This is odd.

Thanks for all the help, though.  I appreciate your time.

---

### Post by rubicon on 2008-01-07
> **~LoKe said:**
> 0 is onboard
1 is soundcard
```
play-file /usr/share/sounds/startup3.wav 0
```
Plays nothing.  Index 1 plays through my headphones.  This is odd.

Thanks for all the help, though.  I appreciate your time.
That's odd. But it's too early to give up!

Can you test your on-board card by speaker-test?
```
speaker-test -c2 -Dhw:0
```
This must produce pink noise on your on-board card, since it is hw:0. Also, try to change subdevice number, like ```
hw:0,0
```

---

### Post by ~LoKe on 2008-01-07
Nothing from that, either. :(

---

### Post by rubicon on 2008-01-07
Well, then it is not a problem with pulseaudio... 

I cannot figure out what it may be, though. Can you test speakers from System > Preferences > Sound? If **this** doesn't work, maybe you just have your speakers unplugged? :)

If you manage to make on-board card work, feel free to continue this thread!

---

### Post by ~LoKe on 2008-01-07
> **rubicon said:**
> Well, then it is not a problem with pulseaudio... 

I cannot figure out what it may be, though. Can you test speakers from System > Preferences > Sound? If **this** doesn't work, maybe you just have your speakers unplugged? :)

Didn't work, either.  This confuses the hell out of me.  I had sound until I started messing with Pulse, and even at one point during, but not anymore.  For the record, I use the s/pdif from my onboard sound to my receiver.  This tells me that I may have screwed up something in .asoundrc. :(

---

### Post by ~LoKe on 2008-01-07
Now I feel especially stupid.  Get sound to playback through alsa by adding this to my .asoundrc:
> pcm.!default {
type plug
slave {
rate 48000
pcm "spdif"
}
}

Now to give pulse another shot...

---

### Post by ~LoKe on 2008-01-07
Adding:
> load-module module-alsa-sink device=spdif:0
To /etc/default.pa
Allows playback!  Woot!  Now to test mpd/mplayer/etc.

MPD works with pulse!

---

### Post by ~LoKe on 2008-01-07
Wicked.  Playing video files with totem and listening to music at the same time.  Excellent.

Now...is there a problem with mplayer that I should be aware of?  I applied the patch and compiled it from svn, but it's still all skippy.

---

### Post by rubicon on 2008-01-07
I'm glad you have a sound, but I don't use mplayer, cannot say what's wrong :) VCL, for one, works fine.

Would you continue struggling with pulseaudio? :)

If so, then I have one question: do pulseaudio server run as system-wide daemon or as per-user instance? Tip: If you haven't changed anything in /etc/default/pulseaudio and neither run it manually somewhere like rc.local, -- then it should be standard one-daemon-per-user option.

---

### Post by ~LoKe on 2008-01-07
Yep, I have to start it manually every time.  I'd prefer to have it run as a daemon, would this be a bad idea?

**EDIT**: VLC would be nice, too, but it won't work either.  I only have ALSA, OSS, Dummy, Jack and Esound.  I thought I could use esound, but it's not playing any audio. :P

---

### Post by rubicon on 2008-01-07
> **~LoKe said:**
> Yep, I have to start it manually every time.  I'd prefer to have it run as a daemon, would this be a bad idea?

**EDIT**: VLC would be nice, too, but it won't work either.  I only have ALSA, OSS, Dummy, Jack and Esound.  I thought I could use esound, but it's not playing any audio. :P
Select 'default', it works for me. ALSA should be OK too.

To run pulseaudio system-wide, you have to edit file '/etc/default/pulseaudio'. There must be such lines:```
# Start the PulseAudio sound server in system mode.
# (enables the pulseaudio init script)
# System mode is not the recommended way to run PulseAudio as it has some
# limitations (such as no shared memory access) and could potentially allow
# users to disconnect or redirect each others audio streams. The
# recommend way to run PulseAudio is as a per-session daemon. For GNOME
# sessions you can install pulseaudio-esound-compat and GNOME will
# automatically start PulseAudio on login (if ESD is enabled in
# System->Preferences->Sound). For other sessions, you can simply start
# PulseAudio with "pulseaudio --daemonize".
# 0 = don't start, 1 = start
PULSEAUDIO_SYSTEM_START=1 #I have already changed this

```

Actually, this file is respected by a script /etc/init.d/pulseaudio.

However, to be able to access sound-server, user must be in pulse-access group, so check this out too.

---

### Post by ~LoKe on 2008-01-07
That seems to have worked, as I heard pulseaudio play the test file when loading GDM.  However...opening paman, once again, says connection refuse.  I tried starting it from the terminal, this is the ouput:
> [13:53:11 loke]$ pulseaudio
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL spdif:0
This is getting ridiculous. ;)

---

### Post by rubicon on 2008-01-07
I didn't get all details (sorry :) ), but that's what should be:
In system monitor: pulseaudio (/usr/bin/pulseaudio --system --daemonize --high-priority *etc...*) user: pulse, priority: -11.
This way you cannot connect to it via pacmd (afaik), but still can run, for one, 'pactl stat' to see status.

What is 'paman'?

Is there any sound in players/something?

What for this problem```
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL spdif:0 
```, we have to localize it.

---

### Post by ~LoKe on 2008-01-07
Hm...I can't get it to run system-wide.  I copied what you gave me into /etc/default/pulseaudio, and verified that I was added to all 3 pulse groups, all that, then rebooted.  I heard the sound again.  Once gnome finished loading, I tried to play sound through MPD.  No joy.  I opened up Pulseaudio Device Chooser, none were listed.  Ran:
```
pactl stat
```
Returned:
> Connection failure: Connection refused

Started "pulseaudio" through the terminal and it started, though it still says:
> ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL spdif:0
But it's "working" now.  MPD plays through my sound device just fine.  But that error makes me think I lost spdif (so no Dobly Digital for my movies).

This is so strange.

---

### Post by rubicon on 2008-01-07
What does system monitor say?

I'm afraid module-alsa-sink just doesn't support "spdif:0"-specification... But that's _the worst_ case, I hope that's not actually so :) After all, there must be some way to access spdif via subdevice number ('hw:0,3', for one).

---

### Post by ~LoKe on 2008-01-07
Rebooted, saw that pulseaudio was starting, logged into gnome, heard the sound again, then checked system monitor.  There's no pulseaudio listed, and mpd doesn't work.  

Sorry for all the trouble.

**EDIT**: I can start pulseaudio manually, which makes me wonder why it won't start automatically.

---

### Post by rubicon on 2008-01-07
> **~LoKe said:**
> Rebooted, saw that pulseaudio was starting, logged into gnome, heard the sound again, then checked system monitor.  There's no pulseaudio listed, and mpd doesn't work.  

Sorry for all the trouble.

**EDIT**: I can start pulseaudio manually, which makes me wonder why it won't start automatically.
Why, this is valuable experience for me! Don't be sorry :)

Let's take a break, and tomorrow I will try to work out something to solve all this...

At least, per-user pulseaudio, like, works :) You may revert the changes and try to edit '/etc/pulse/daemon.conf' and set realtime-scheduling for daemon, this may solve sound distortions and underruns,

---

### Post by ~LoKe on 2008-01-07
Err...I feel like an idiot.  I'm not entirely sure, but I may have improperly added myself to the groups.  I looked at system log and it's full of "operation not permitted".

Before you go (if you don't mind), could you possibly tell me how to properly add myself to the group?

---

### Post by rubicon on 2008-01-07
Don't mind the log. It is flooded constantly, there's a bug in pulseaudio (it's on the launchpad). Bugtracker on pulseaudio site, however, says it is closed (some odd explanation given), but it is still there, logs flooded...

To add a user to groups:```
sudo adduser loke pulse-access && sudo adduser loke pulse-rt
groups loke # to see what groups you are in

```

---

### Post by rubicon on 2008-01-07
Oh, better run separately:```

sudo adduser loke pulse-access
sudo adduser loke pulse-rt

```

---

### Post by ~LoKe on 2008-01-07
It works!  I've got mplayer over spdif/pulse playing without skipping.  This was the solution:
> mplayer dvd:// -ao alsa:device=spdif -ac hwac3
Solved my mplayer issues!  Now I have to save this all to a file so I can fix everything if something comes up.  Thanks for all your help, it definitely got me here!

---

### Post by rubicon on 2008-01-08
I see, after all you use ALSA, not PulseAudio...

---

### Post by ~LoKe on 2008-01-08
> **rubicon said:**
> I see, after all you use ALSA, not PulseAudio...

Yeah I noticed that a bit after I posted.  ](*,)  Thought I was reading a pulseaudio guide and saw that line and it worked...but it was an audio guide for s/pdif, not PA.  Grr.

---

