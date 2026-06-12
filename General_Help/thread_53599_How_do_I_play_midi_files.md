---
title: "How do I play midi files?"
date: 2005-08-01
forum: General Help
---

### Post by geokker on 2005-08-01
How do I play midi files? I've installed xplaymidi but nowt happens when I try to use it.

I get this error from the command line:

open /dev/sequencer: No such file or directory

What gives?

I've got a Soundblaster Live! Value which seems to work in all other respects.

---

### Post by jdodson on 2005-08-01
[QUOTE=geokker]How do I play midi files? I've installed xplaymidi but nowt happens when I try to use it.

I get this error from the command line:

open /dev/sequencer: No such file or directory

What gives?

I've got a Soundblaster Live! Value which seems to work in all other respects.[/QUOTE]

do a forum search for "midi howto," worked for me.

---

### Post by geokker on 2005-08-07
None of the howto's really helped. In the end, I installed kmid and pfaffed about with the midi setup in the gui. 

So no 

$ sudo -u -h -j -x -q -b -n -v loadsfx -d -f snd_midi:0x53463HH | midialsa -fg -h /d /fr /ee Emu10k1 load -val 10 channel 1 -xc

shenanigans for me!

---

