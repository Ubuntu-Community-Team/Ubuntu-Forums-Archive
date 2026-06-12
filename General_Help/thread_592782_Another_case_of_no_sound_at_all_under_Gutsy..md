---
title: "Another case of no sound at all under Gutsy."
date: 2007-10-26
forum: General Help
---

### Post by HippoMan on 2007-10-26
I'm another person who lost all sound when upgrading from Feisty to Gutsy.  I checked everywhere I could, including the following pages:[INDENT][http://ubuntuforums.org/showthread.php?t=205449&highlight=gutsy+no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=gutsy+no+sound)
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
[/INDENT]However, nothing I tried could re-enable my sound capabilities.  Therefore, here I am.

When reading the following discussion, you can refer to the Pastebin output of my run of the ALSA Information Script here: [http://pastebin.ca/750760](http://pastebin.ca/750760)

I have a **Dell XPS 410**, and I'm running **kubuntu**, kernel **2.6.22-14-generic #1 SMP**.

```
 $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```I presume that this means that my sound device is **snd-hda-intel**.  Here is
the Audio section of the lspci output:```
$ lspci -vvnn
...
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
        Subsystem: Dell Unknown device [1028:01db]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
...
```Why am I getting **<access denied>**?
```
$ ls -l /dev/*snd*
wxrwxrwx 1 root root  24 Oct 26 14:26 /dev/sndstat -> /proc/asound/oss/sndstat

/dev/snd:
total 0
crw-rw---- 1 root audio 116, 8 Oct 26 14:26 controlC0
crw-rw---- 1 root audio 116, 7 Oct 26 14:26 hwC0D2
crw-rw---- 1 root audio 116, 6 Oct 26 14:26 pcmC0D0c
crw-rw---- 1 root audio 116, 5 Oct 26 14:26 pcmC0D0p
crw-rw---- 1 root audio 116, 4 Oct 26 14:26 pcmC0D1p
crw-rw---- 1 root audio 116, 3 Oct 26 14:26 seq
crw-rw---- 1 root audio 116, 2 Oct 26 14:26 timer

$ ls -l /dev/*dsp*
crw-rw---- 1 root audio 14, 12 Oct 26 14:26 /dev/adsp
crw-rw---- 1 root audio 14,  3 Oct 26 14:26 /dev/dsp
```I'm running as a user called "hippo", and here's the "audio" entry in /etc/group:```
audio:x:29:hippo
```Here's more stuff:```
$ tail -2 /proc/asound/oss/sndstat
Mixers:
0: SigmaTel STAC9227

$ modinfo snd_hda_intel
filename:       /lib/modules/2.6.22-14-generic/updates/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     7C05112D0C9214E90DF6E16
alias:          pci:v000010DEd00000777sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000776sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000775sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000774sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FCsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Csv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd,snd-hwdep,snd
vermagic:       2.6.22-14-generic SMP mod_unload 586
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           index:Index value for Intel HD audio interface. (int)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           model:Use the given board model. (charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)
parm:           enable:bool

$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 0 [0%] [-95.25dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Analog Loopback',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',2
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Swap Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
fuse
snd-hda-intel
```I ran **alsamixer**, and it shows all the controls and gives me no errors.  I set **Master**, **PCM**, **Front**, **Surround**, **Center**, **LFE**, and **Side** to 100%, and I still don't hear anything.

Just in case, I rebuilt my kernel as described in the _**[SIZE=3]Getting the ALSA drivers from a *fresh* kernel[/SIZE]**_ section of the **Comprehensive Sound Problems Solutions Guide**, whose link I included above. I also uninstalled and reinstalled **linux-sound-base**, **alsa-base**, and **alsa-utils**, also as decribed in that guide. None of those things helped, either.

Does anyone have an idea what's going on with my setup and what I can do to get my sound back?

I've tried to include every piece of information that might be pertinent.  However, if there's still anything I left out that could help, please let me know.

Thank you all very much, in advance, for any help you might be able to offer.
[RIGHT].
[/RIGHT]

---

### Post by vapore0n on 2007-10-26
if you go to System/Preferences/Sound and do a test, does it come out with and error, or does it just not sound?

In my laptop I had to enable External Amplifiyer in the volume controll options, else I would not get any sound.
Also, sound used to work on Alsa, then ESS, and now is on OSS.

---

### Post by HippoMan on 2007-10-26
Thanks for your quick response!

I'm running **kubuntu**, and there is no **System/Preferences/Sound** section.  In fact, there's no section called **Preferences** at all under **System**, and nothing that pertains to sound.  Could that be part of my problem?

Also, there unfortunately are no controls that pertain to any kind of external amplifier on my system.
[RIGHT].
[/RIGHT]

---

### Post by HippoMan on 2007-10-26
PS: when I try to do anything that involves sound, such as play a music file, the program always indicates no error, and the console output states that the sound is happily playing without any problem.

It's as if my sound card is correctly accepting all input passed to it, but simply not generating any output.

Also, in my ROM BIOS, it states that the sound card is properly turned on.
[RIGHT].
[/RIGHT]

---

### Post by cmargolin on 2007-10-26
After upgrading to Gutsy and bringing up alsamixer, I found that everything was muted.  Unmuting solved my sound problem.

---

### Post by HippoMan on 2007-10-26
Thanks.  However, I don't see anything being muted.  As I mentioned above, everything in **alsamixer** shows levels at 100%.  **KMix** shows the same.

Is there another place to go under **kubuntu** to unmute the audio?

[RIGHT].
[/RIGHT]

---

### Post by HippoMan on 2007-10-26
Well, this turns out to be related to the kernel.  If I reboot under the older, **2.6.20-16-generic #2 SMP** kernel, the sound works fine again.  Everything else is identical.

So ... could someone point me to some docs that will help me figure out what the pertinent differences are between that older kernel and the newest one (**2.6.22-14-generic #1 SMP**), and which provide instructions about how to fix the newer kernel so that sound works the same way as in the older one?

Thanks again.
[RIGHT].
[/RIGHT]

---

### Post by HippoMan on 2007-10-27
Given that this seems to be a kernel problem, I have now posted a bug report in Launchpad:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/157730](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/157730)

Nonetheless, if anyone here has any insight as to how I might fix this, please do post your ideas here.

Thanks again to all.
[RIGHT].
[/RIGHT]

---

### Post by adamorjames on 2007-10-27
Yeah, I have a Kernel problem too with Gutsy. HDA Intel, soft sound. Changed Kernel to an older Kernel(which I think was from Tribe 5) and sound went back to normal. 
Things just get broken. :lolflag: So, mark this thread as "[SOLVED]".

---

### Post by HippoMan on 2007-10-27
I'm glad to know I'm not alone here.  Yep, sh*t happens ... :)

... although I won't mark this as "SOLVED" until I get some feedback on the bug report.  Who knows, maybe they actually have a solution by now that I can share with everyone here.

Thanks a lot.
[RIGHT].
[/RIGHT]

---

### Post by zeltak on 2007-10-29
Hi

ive got exactly the same problems as you guys (using kubuntu as well)  but i just made a fresh install on my new comp and i dont have a "previous" kernel...so for me its definantly no sound. i hope some one can come up with an answer soon

Zeltak

---

### Post by adamorjames on 2007-10-29
> **zeltak said:**
> Hi

ive got exactly the same problems as you guys (using kubuntu as well)  but i just made a fresh install on my new comp and i dont have a "previous" kernel...so for me its definantly no sound. i hope some one can come up with an answer soon

Zeltak

I wonder if I could upload my kernel to a website to help you... not sure Or, maybe you could use the Tribe 5 CD and get the kernel from it. I'm not too sure how kernels work.

---

### Post by HippoMan on 2007-11-20
I finally have a solution.

First of all, it turns out that the 2.6.22-14-generic kernel was indeed muting the sound card upon startup.  I didn't see that because I use KDE, and the KMix application shows a 100-percent volume level, which I incorrectly assumed to mean that the card is not muted.  There are no indicators on KMix to show the muting state, and only when someone suggested that I run gnome-alsamixer did I see that the channels were indeed muted.

After un-muting from within gnome-alsamixer, sound started working fine under 2.6.22-14-generic.

This muting behavior at startup is the opposite of what takes place in the older 2.6.20-16-generic kernel, which would always initialize the sound card in the un-muted state.

I don't want to have to remember to manually un-mute the sound card after each reboot, and so I have arranged for the following command to run as part of my system startup sequence:[INDENT]**/usr/bin/amixer -q set Front '100%' unmute**
[/INDENT]This ensures that the sound card always starts up unmuted.

So ... all's well that ends well.

Thanks to all.
[RIGHT].
[/RIGHT]

---

