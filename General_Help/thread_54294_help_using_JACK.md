---
title: "help using JACK"
date: 2005-08-04
forum: General Help
---

### Post by ign on 2005-08-04
im trying to setup oddcast ( [http://www.oddsock.org/tools/oddcastv3_jack/](http://www.oddsock.org/tools/oddcastv3_jack/) ) to stream from my computer using XMMS.

oddcast needs JACK to be working, so i'm trying to configure it using qjackctl. when i run it i get the following error message:

"Warning: no locale found: /usr/share/locale/qjackctl_es_ES.UTF-8.qm"

then i get a pop up with this message:

"Error Could not open ALSA sequencer as a client. MIDI patchbay will not be available"

i don't need midi, anyway. i also get this message on JACK's message window (i can't tell if it's the same error):

"ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No existe el fichero o el directorio"

once open i can't see anything in the "connect" window, so i suppose it's not working.

i've also installed XMMS-JACK, but when i configure the properties in XMMS to use JACK as output i get an error message:

rough translation (my system is in spanish): "please verify that: your souncard is properly configured, you have selected the correct output plugin, there are no other programs blocking the soundcard"

---

### Post by johannes on 2005-08-04
I managed to get qjackctl working, but I can't remember exactly how. You can try this though:

killall esd

sudo qjackctl

If it doesn't work, try the advices from [this](http://www.ubuntuforums.org/showthread.php?t=27170&highlight=qjackctl) thread.

---

