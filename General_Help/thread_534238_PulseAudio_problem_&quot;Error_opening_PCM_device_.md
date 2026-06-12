---
title: "PulseAudio problem &quot;Error opening PCM device default: Connection refused&quot;"
date: 2007-08-25
forum: General Help
---

### Post by KernelPanic14 on 2007-08-25
I installed the package PulseAudio, and followed PulseAudio "PerfectSetup" ([http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup))
It worked for 2 days, but it started failing with an error about hw:0 connection refused or something like that.
So, I changed load-module module-alsa-sink device=hw:0 to load-module module-alsa-sink.
It worked again, but only for 3 days.
I now have this problem:
[quote=GNOME Terminal 2.18.0 with 'sudo -s']main.c: This program is not intended to be run as root (unless --system is specified).
alsa-util.c: device doesn't support 44100 Hz, changed to 48000 Hz.
alsa-util.c: device doesn't support 44100 Hz, changed to 48000 Hz.
*** PULSEAUDIO: Unable to connect: Timeout
module-alsa-sink.c: Error opening PCM device default: Connection refused
module.c: Failed to load  module "module-alsa-sink" (argument: ""): initialization failed.
*** PULSEAUDIO: Unable to connect: Timeout
module-alsa-source.c: Error opening PCM device default: Connection refused
module.c: Failed to load  module "module-alsa-source" (argument: ""): initialization failed.
main.c: Module load failed.
main.c: Module load failed.[/quote]
And it says this when i run without sudo:
[quote=GNOME Terminal 2.18.0 without sudo -s]main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
module-alsa-sink.c: Error opening PCM device hw:0: No such device
module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0 sink_name=alsa_output.pci_8086_2485_alsa_playback_0"): initialization failed.
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
module-alsa-source.c: Error opening PCM device hw:0: No such device
module.c: Failed to load  module "module-alsa-source" (argument: "device=hw:0 source_name=alsa_input.pci_8086_2485_alsa_capture_0"): initialization failed.
oss-util.c: open('/dev/dsp'): Permission denied
module.c: Failed to load  module "module-oss" (argument: "device=/dev/dsp sink_name=oss_output.pci_8086_2485_oss_pcm_0_0 source_name=oss_input.pci_8086_2485_oss_pcm_0_0"): initialization failed.
module-hal-detect.c: failed to detect any sound hardware.
module.c: Failed to load  module "module-hal-detect" (argument: ""): initialization failed.
main.c: Module load failed.
main.c: failed to initialize daemon.[/quote]
I changed again to hw:0,0, but now it says the same about connection refused :(.
This is my /etc/default.pa file:
```
#!/usr/bin/pulseaudio -nF 

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


### Load audio drivers statically
#load-module module-alsa-sink device=hw:0
#load-module module-alsa-source device=plughw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

.ifexists /usr/lib/pulse-0.9/modules/module-hal-detect.so

### Automatically load driver modules depending on the hardware available
load-module module-hal-detect

.else

### Alternatively use the static hardware detection module (for systems that
### lack HAL support
load-module module-detect

.endif

### Load audio drivers automatically on access
#add-autoload-sink output module-oss device="/dev/dsp" sink_name=output source_name=input
#add-autoload-source input module-oss device="/dev/dsp" sink_name=output source_name=input
#add-autoload-sink output module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#add-autoload-source input module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#add-autoload-sink output module-alsa-sink sink_name=output
#add-autoload-source input module-alsa-source source_name=input

.ifexists /usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so

### Load esound protocol
load-module module-esound-protocol-unix

.endif

### Load native protocol
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

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make some devices default
#set-default-sink output
#set-default-source input

.nofail

### Load something to the sample cache
load-sample x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-dir-lazy /usr/share/sounds/*.wav

### Load X11 bell module
load-module module-x11-bell sample=x11-bell

### Publish connection data in the X11 root window
load-module module-x11-publish

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
#load-module module-gconf
load-module module-alsa-sink
load-module module-alsa-source
```
And this is my asound.conf:
```
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```
(I don't have any problem with the 44100 Hz, but if someone can help me with the connection refused, it would be better if it also helps me with 44100, hal when not root, group pulse-rt, oss when not root and pulseaudio using hw:0 (which i don't want) when not root).

---

### Post by KernelPanic14 on 2007-08-25
Uh, i forgot saying, I'm running Feisty Fawn 32bits
I have a Dell Inspiron 2650, i think it has a 1.7Ghz Celeron or Pentium4 and it has an NVIDIA NV11 Geforce2Go (which i think you don't need to know because the problem is with sound :p)

---

### Post by KernelPanic14 on 2007-08-25
Any Help?

---

### Post by KernelPanic14 on 2007-08-25
Any Help?!
Sorry If I post alot, but this is REALLY URGENT!

---

### Post by KernelPanic14 on 2007-08-26
bump
people here only help 'selected users'!
Why? That's a very idiot way of being!
I might better post in PulseAudio Forum (if they have), because here no one helps.

---

### Post by KernelPanic14 on 2007-08-26
Forget it, i'm going to migrate to Debian ! MUAHAHAAHAHAHAAH!
well, yes, i'm changing to debian, i have had alot of problems with ubuntu, so i'm going to change to debian.

---

### Post by pek on 2007-11-04
same problem here :|

---

### Post by KernelPanic14 on 2007-11-04
Forget it. Moved to Debian. It was horrible, a nightmare! I reinstalled Ubuntu, and it worked like a charm.
Now i'm on Ubuntu Gutsy and I love it, and I don't have anymore PulseAudio problems! (and I'm still using  PulseAudio)
But I'm still upset because it took months for someone to reply and it wouldn't have helped me

---

### Post by hackeron on 2007-11-08
Errrr, so what's the solution? -- I'm having the same problem

---

### Post by KernelPanic14 on 2007-11-09
> **hackeron said:**
> Errrr, so what's the solution? -- I'm having the same problem

Did you read my post?

[QUOTE=me]Forget it. Moved to Debian. It was horrible, a nightmare! **I reinstalled Ubuntu**, and it worked like a charm.
Now i'm on Ubuntu Gutsy and I love it, and I don't have anymore PulseAudio problems! (and I'm still using PulseAudio)
But I'm still upset because it took months for someone to reply and it wouldn't have helped me[/QUOTE]

I hope I knew the solution... So either reinstall, wait for help (might never come), or stop using PulseAudio (switch to something like JACK or return to plain ALSA... is JACK as good as PulseAudio?)

---

### Post by hackeron on 2007-11-09
> **KernelPanic14 said:**
> Did you read my post?
I hope I knew the solution... So either reinstall, wait for help (might never come), or stop using PulseAudio (switch to something like JACK or return to plain ALSA... is JACK as good as PulseAudio?)

I found my problem on pulseaudio bug list. The problem is pulseaudio 0.9.6 doesn't support 24bit audio cards, so people with cards like the M-Audio Revolution 5.1 or 7.1 need to upgrade to 0.9.7 manually until ubuntu have a package.

---

### Post by qntal on 2008-02-09
same problem here... gutsy 32bit and realtek ac883. it just stopped working... i hate when this things happen.

---

### Post by Megatog615 on 2008-03-12
*BUMP*

Still no solution?
```
$ pulseaudio 
*** PULSEAUDIO: Unable to connect: Connection refused
E: alsa-util.c: Error opening PCM device default: Connection refused
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=default"): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

```
I disabled the HAL module for pulseaudio and switched to module-alsa-sink/source with device=default. Inspiron 2650, here(same as a previous user).

---

### Post by rockyraccoon on 2008-03-15
hey, i was having this same problem, i may be able to help you. i assume you installed pulseaudio with synaptic from the repositories. the problem with this is that it is an older version of pulseaudio 0.9.6. I read somewhere that the connection refused problem was a bug with the older version that was fixed in the newer. i installed the 0.9.9 debs that someone compiled and linked in this thread> [http://ubuntuforums.org/showthread.php?t=658044&page=2&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=658044&page=2&highlight=pulseaudio)
i then followed the setup instructions which you can find on the pulseaudio site or floating around the net (google). and now i connect and get sound.

i'm still having trouble getting it to use my pci soundcard instead of the onboard chip. getting there though!


edit: i forgot to mention, i uninstalled the 0.9.6 packages first, although  i'm not sure if its necessary. i think the new ones might conflict if you don't.

---

