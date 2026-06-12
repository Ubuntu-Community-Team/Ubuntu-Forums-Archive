---
title: "MusE"
date: 2006-11-13
forum: General Help
---

### Post by dbbolton on 2006-11-13
> MusE failed to initialize the Alsa midi subsystem, check your configuration.


what is this?

---

### Post by musicinmybrain on 2006-11-13
MusE is a MIDI sequencer. Ubuntu doesn't come configured with MIDI support. Some sound cards, like the Audigy series, have Linux-compatible hardware synthesis. Most likely, however, you'll need to set up a software synthesizer like Timidity. Fortunately, this is documented [on the Ubuntu wiki]("https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo").

---

### Post by dbbolton on 2006-11-13
yeah, i have timidity. i guess it's not really a huge dilemma. i can deal. thanks though.

some programs under "add/remove applications" have proven to be a bit questionable for me.

---

### Post by flatko on 2006-12-01
I've got both Muse and Timidity on my Dapper, but Muse shows only the start screen and that's all...
So, i tried starting it from the command line. It returns the following:

flatko@flatko-desktop:~$ muse
No superuser privileges, using system timer fallback
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
NO Config File </home/flatko/.MusE> found
no locale <muse_bg_BG.UTF-8>/</usr/share/muse/locale>
Trying RTC timer...
RtcTimer::setTimerFreq(): cannot set tick on /dev/rtc: Permission denied
  precise timer not available
Trying ALSA timer...
got timer = 12
QObject::connect: No such signal PartCanvas::horizontalScroll(int)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'unnamed')
Arranger::configChanged - no bitmap!
open projectfile: No such file or directory
starting with default template
  name2route: <alsa_pcm:playback_1> not found
  name2route: <alsa_pcm:playback_2> not found
Arranger::configChanged - no bitmap!
AlsaTimer::setTimerTicks(): requested freq 1024 Hz too high for timer (max is 250)
  freq stays at 250 Hz
Segmentation fault


Does anybody know what this mean?
Thanks in advance.

---

### Post by yippy on 2007-01-17
I have exactly the same problem.  Was a solution ever found?

---

### Post by dbbolton on 2007-01-17
not as far as i know

---

### Post by sgx on 2007-01-21
This may be a kernel that has timings that are not midi compatible, a Fedora
kernel and Rosegarden had what appears to be the samr issue in the past.
Maybe try the realtime kernel crafted skillfully by Luneo...and google search the
relevant terms for tips on modifying the timing...hope this helps.

---

