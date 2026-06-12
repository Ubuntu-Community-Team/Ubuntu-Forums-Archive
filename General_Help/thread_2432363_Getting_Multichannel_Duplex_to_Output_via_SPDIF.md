---
title: "Getting Multichannel Duplex to Output via SPDIF"
date: 2019-12-01
forum: General Help
---

### Post by drsaamah on 2019-12-01
Using UbuntuStudio 18.04.3 with a Focusrite Scarlett 18i20 as my soundcard. I just recently upgraded to 18.04 and I was excited to see that pulse audio now recognizes and allows me to use the Scarlett as my soundcard for applications other than Ardour.  The problem is that my monitors are connected to the SPDIF output on the Scarlett and I cannot for the life of me figure out how to get the system sounds and application sounds to output via SPDIF instead of the analog outputs on the Scarlett.  The SPDIF works fine in Ardour (they are recognized as Output Channels 11 & 12).  But for everything else, pulse is outputting on analog outputs 1-10, sending nothing to SPDIF.

---

### Post by SeijiSensei on 2019-12-02
Try installing pavucontrol which lets you control which channels to use for audio input and output.

---

### Post by drsaamah on 2019-12-02
Yeah I'm using pavucontrol.  The "channels" it shows are "Front Left", "Front Right", "Rear Left", etc which are all set to 100%(0.00dB) with nothing going through the SPDIF output.  All ten of the analog outputs are putting out sound, but SPDIF is silent.

---

### Post by SeijiSensei on 2019-12-03
Actually it's the "port" that matters.

[img]https://www.politicsbythenumbers.org/images/pavucontrol.png[/img]

Mine is set to "HDMI Displayport."  Is the SPDIF device not in the list for you?

---

### Post by drsaamah on 2019-12-03
Yes.  The port is set to the "Scarlett 18i20 Multichannel".  And in pavucontrol it'll show that it is receiving signal.  Again, that signal is actually getting sent to the Focusrite, but it is only outputting on the analog outputs.  The SPDIF output is putting out nothing.  The SPDIF does work, because that is how I am monitoring everything with Ardour.

---

### Post by drsaamah on 2019-12-07
*bump* Nobody has any idea how this might be resolved?

---

