---
title: "Audio selection"
date: 2016-10-07
forum: General Help
---

### Post by geomcd1949 on 2016-10-07
Ubuntu 16.04
Each time my machine restarts or suspends, the selected audio reverts to Digital Output (S/PDIF) from HDMI/DisplayPort 3.
Is there a way to stop this?
Thanks!
~George

---

### Post by Kris_M on 2016-10-08
Disconnect that cable from your computer except when you are going to use it?

---

### Post by Bucky Ball on 2016-10-08
Open Pulseaudio volume control and go to the 'Configuration' tab. How is that set up? You should have two entries there, top and bottom.

---

### Post by geomcd1949 on 2016-10-08
I run a dual-monitor setup. Each monitor has its own speakers built-in. They are listed in Sound Settings as
HDMI/DisplayPort3 - GK104 HDMI Audio Controller
and
HDMI/DisplayPort3 - GK104 HDMI Audio Controller.

The third listing in Sound Settings is Digital Output (S/PDIF) Built-In Audio.

There are no speakers connected to the motherboard output jacks in the rear of the computer. [So, Kris_M, thank you, however, no cable to disconnect.]

In Sound Settings, I highlight HDMI/DisplayPort3 - GK104 HDMI Audio Controller and my audio plays properly through the monitor's speakers.

When I shut down or restart the computer, the Digital Output (S/PDIF) Built-In Audio becomes highlighted, and no audio will play until I go into Settings and highlight HDMI/DisplayPort3 - GK104 HDMI Audio Controller.

In Pulse Audio Volume Control > Configuration, the top listing is  GK104 HDMI Audio Controller with a Profile of Digital Stereo (HDMI 3) Output.

The lower listing in Pulse Audio is Built-in Audio with a Profile of Digital Stereo (IEC958) Output + Analog Stereo Input.

I don't see any method of setting the default speakers, but have never had this issue until upgrading from 14.04 LTS to 16.04 LTS.

~George

---

