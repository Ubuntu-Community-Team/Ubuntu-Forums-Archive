---
title: "Crackling sound whenever activating the sound"
date: 2016-09-27
forum: General Help
---

### Post by guccimucci on 2016-09-27
Hello!

Whenever I unmute the sound or boot-up the laptop with sound unmuted I hear a "crackling" sound through the speakers. I've read that this is probably caused by the sound powersaving (and tlp), which means, that whenever sound is activated it makes a sound, but it is quite annoying, because for example when I get a facebook message it always does the 'crack' sound first and then the notification sound. Is it possible to somehow disable the crack sound or extend the time while sound is active so it doesn't fall to powersaving mode in couple of seconds? Overall, what is causing this problem and is it really 'tlp' problem or could it be something else?

So far I've tried disabling soundcard powersaving and several other things I've found while googling the problem. I somehow managed to fix the problem in my previous install, but then I messed up the sound configuration, which eventually led me to reinstall. As far as I am concerned this problem is quite  frequent, but I'd like to know what is causing this and how to fix it. I'm now smarter and I've backed up the system before I change anything through terminal.

I'm running Ubuntu MATE 16.04 on Dell Latitude E7470. The same thing happened with another laptop in Ubuntu 14.04 and I couldn't fix it back then too. My sound card information is the following (using lscpi -v command):

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: Dell Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 132
    Memory at e1348000 (64-bit, non-prefetchable) [size=16K]
    Memory at e1320000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

I think it is not a soundcard specific problem as it has happened with many people from different hardwares. I've read that it's a kernel problem, but I'm looking forward for your ideas and help.

Thanks in advance!

---

### Post by #&amp;thj^% on 2016-09-27
I had a friend with the same Dell Latitude E7470
I found a solution by toying around with the alsamixer.

For me the solution is to disable the loopback channel.

Start alsamixer with this command:
```
alsamixer -c0

```
   1. Navigate to the Loopback channel rightmost with arrow-key
   2. Disable the Channel by pressing the arrow-down-key once
   3. Save and quit the alsamixer with ESC

After that you need to reboot. The crackle is gone.
See Screenshot.

---

### Post by guccimucci on 2016-09-28
As simple as that. Thanks!

---

### Post by #&amp;thj^% on 2016-09-28
:) Your Welcome.
If you are satisfied with the solution...please mark the thread as solved to help future visitors.
Kind Regards

---

