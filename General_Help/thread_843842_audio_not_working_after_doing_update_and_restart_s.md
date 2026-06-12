---
title: "audio not working after doing update and restart system.."
date: 2008-06-28
forum: General Help
---

### Post by Mia_tech on 2008-06-28
after doing update and restarting, I got no audio, I click on the audio control, and I get error:
```
No volume control GStreamer plugins and/or devices found.
```
also get this error

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

I went to synaptic and the gstreamer plugins are installed for the alsa
here's my sound card
```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```any help appreciated

thanks

---

### Post by Mia_tech on 2008-06-29
I finally got it working by this guide

[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

---

