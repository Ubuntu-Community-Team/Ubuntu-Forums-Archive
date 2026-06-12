---
title: "No audio with DVDs???"
date: 2005-10-21
forum: General Help
---

### Post by audax321 on 2005-10-21
I just noticed that I can play DVDs on Totem, but I get NO audio output. I have libdvdcss2 and w32codecs installed and avi/mpg files play fine with audio and everything. But DVDs have no audio, just video. Any ideas?

---

### Post by Emerzen on 2005-10-21
When I lose audio, I usually go to Preferences and change my audio drive -> OSS vs ALSA vs ESD.  Have you tried that yet?  Are you running Breezy?

---

### Post by audax321 on 2005-10-21
Just tried that but its not working. Audio in general is working. I can play music, avi, mpg audio/video and everything. The only problem is DVD audio. This worked fine under Hoary, but after formatting and installing Breezy its just doesn't play DVD audio anymore. Is there a codec I'm missing or something??? :confused:

---

### Post by audax321 on 2005-10-21
FIXED!!!

This is what I did:

1. Open synaptic and completely remove w32codecs and libdvdcss2

2. In the home folder, removed:
  .dvdcss
  .xine
  .gnome2/totem-addons
  .gnome2/totem_config

3. In a terminal:
  gst-register-0.8

4. In the home folder, removed:
  .gstreamer-0.8

5. Rebooted

6. In synaptic, reinstalled w32codecs, libdvdcss2, and EVERY gstreamer package (didn't actually install every gstreamer package, just reinstalled the ones I already had installed)

7. In a terminal:
  gst-register-0.8

8. Reboot

After this I got my audio back :)

---

### Post by audax321 on 2005-10-31
Some warning: Using the above method gave my audio back with DVDs but my audio for MP3s, WAVs, etc got really garbled. Instead some people have had luck installing vlc and vlc-plugin-alsa. I've since had to reinstall to fix my sound issues.

---

