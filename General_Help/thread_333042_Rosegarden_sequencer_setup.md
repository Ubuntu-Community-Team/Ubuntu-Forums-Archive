---
title: "Rosegarden sequencer setup"
date: 2007-01-06
forum: General Help
---

### Post by Bushfire on 2007-01-06
Hi,
I am attempting to get rosegarden4 working. However, it cannot start the sequencer, and I'm am unsure of the reason.

I start jack with this command:

```
$ jackd -d alsa
```

and get this:

```

jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead

```

That seems to be enough for other programs requiring the jack server but,
when I run:

```

$ rosegardensequencer

```

I get this output:

```

rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-bernard//rosegarden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb6357000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.8

JackDriver::initialiseAudio - JACK sample rate = 48000Hz, buffer size = 1024
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "alsa_pcm:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "alsa_pcm:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

Any ideas?

Thanks in advance,
-Bernard.

---

### Post by eric71 on 2007-01-08
Jack seems to be working, but rosegarden is complaining that the Alsa sequencer is not loaded.  This is not loaded by default in Ubuntu.  Check out the studio set up tutorial here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

ALSA Sequencer
If you are planning on using MIDI at all, you will want to load the ALSA sequencer module. 
 sudo modprobe snd-seq

To have your system load it at bootup, you have to add it to the /etc/modules file. 
 sudo su -c 'echo snd-seq >> /etc/modules'

---

### Post by rogerf on 2007-01-11
I have been following this thread with interest as I want to get rosegarden working on my Ubuntu dist. I put in your recomended suggestions and now rosegarden will import midi files but no sound comes out! Is there some setting i should make. If i type
timidity file.mid
Then I hear the midi file fine. So the fault must lie with how i am using rosegarden.


> **eric71 said:**
> Jack seems to be working, but rosegarden is complaining that the Alsa sequencer is not loaded.  This is not loaded by default in Ubuntu.  Check out the studio set up tutorial here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

ALSA Sequencer
If you are planning on using MIDI at all, you will want to load the ALSA sequencer module. 
 sudo modprobe snd-seq

To have your system load it at bootup, you have to add it to the /etc/modules file. 
 sudo su -c 'echo snd-seq >> /etc/modules'

---

