---
title: "What is /dev/snd/seq and how do I make it work?"
date: 2005-06-14
forum: General Help
---

### Post by alive on 2005-06-14
I've used two separate programs now that give me a message similar to this:

ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

The first was Dosbox, which seemed to work anyway; the second is Rosegarden, which then prints this endlessly, and, needless to say, doesn't work:

rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up

How do I make /dev/snd/seq exist so the sequencer can come up?

Many thanks in advance.

---

### Post by skoal on 2005-06-14
sudo modprobe snd-seq

\\//_

---

### Post by alive on 2005-06-14
Thank you.

---

