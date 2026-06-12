---
title: "Java Sound Configuration Problem /etc/java-x.x.x-sun/sound.properties"
date: 2007-10-12
forum: General Help
---

### Post by mig5 on 2007-10-12
Hi,
I posted this problem before, but in a much more generalized problem thread (called "Java: Sound in Blackdown, No Sound in Sun. Blackdown Freezes").  At the time, I didn't know what was causing the sound not to work in Sun Java JREs 1.5 and 1.6 .  Now I do.

In a Sun Java installation there is a sound configuration file called '*sound.properties*' which is located under */etc/java-x.x.x-sun/* (the x being the version numbers).  Normally you don't need to edit this file because the sound devices should automatically be detected.  However, for me this is not the case.

I need help adding the correct information to this file to make java MIDI sound work (someone has already explained to me how to get java sampled sound to work).  For the whole story, check out my original thread: [http://ubuntuforums.org/showthread.php?t=497589](http://ubuntuforums.org/showthread.php?t=497589)

Here is the current contents of my */etc/java-6-sun/sound.properties* file (only the last 4 lines were added by me):

```

############################################################
#               Sound Configuration File
############################################################
#
# This properties file is used to specify default service
# providers for javax.sound.midi.MidiSystem and
# javax.sound.sampled.AudioSystem.
#
# The following keys are recognized by MidiSystem methods:
#
# javax.sound.midi.Receiver
# javax.sound.midi.Sequencer
# javax.sound.midi.Synthesizer
# javax.sound.midi.Transmitter
#
# The following keys are recognized by AudioSystem methods:
#
# javax.sound.sampled.Clip
# javax.sound.sampled.Port
# javax.sound.sampled.SourceDataLine
# javax.sound.sampled.TargetDataLine
#
# The values specify the full class name of the service
# provider, or the device name.
#
# See the class descriptions for details.
#
# Example 1:
# Use MyDeviceProvider as default for SourceDataLines:
# javax.sound.sampled.SourceDataLine=com.xyz.MyDeviceProvider
#
# Example 2:
# Specify the default Synthesizer by its name "InternalSynth".
# javax.sound.midi.Synthesizer=#InternalSynth
#
# Example 3:
# Specify the default Receiver by provider and name:
# javax.sound.midi.Receiver=com.sun.media.sound.MidiProvider#SunMIDI1
#
javax.sound.sampled.Clip=#AudioPCI [plughw:0,0]
javax.sound.sampled.Port=#Port AudioPCI [hw:0]
javax.sound.sampled.SourceDataLine=#AudioPCI [plughw:0,0]
javax.sound.sampled.TargetDataLine=#AudioPCI [plughw:0,0]

```

Edit: the rest of this page and most of page 2 is just bumps, so you can skip those if your like.

---

### Post by mig5 on 2007-10-13
[COLOR="Gray"]bump[/COLOR]

---

### Post by mig5 on 2007-10-14
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-10-15
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-10-16
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-10-17
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-10-19
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-10-22
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-11-02
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-11-14
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-11-17
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-11-24
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-11-27
[COLOR="Gray"]bump[/COLOR]

---

### Post by mig5 on 2007-12-03
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-12-09
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2007-12-20
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2008-01-02
[COLOR="Gray"]Bump[/COLOR]

---

### Post by mig5 on 2008-02-02
[COLOR="Gray"]Bump[/COLOR]

---

