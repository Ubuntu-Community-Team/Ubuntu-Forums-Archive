---
title: "Libreoffice video hang."
date: 2013-10-24
forum: General Help
---

### Post by Jumphog on 2013-10-24
Tried to add this to the first result on a google search but the thread is closed, so here are some notes:

Libreoffice 4.0.2.2 on a fresh install of Xubuntu 13.04

Presentations that worked on my old install wouldnt work any more - mpg2 videos would only show a grey box, and not play.
The fix for this is to make sure that these are installed:

gstreamer1.0-plugins-good
gstreamer1.0-plugins-bad
gstreamer1.0-plugins-ugly
gstreamer1.0-pulseaudio

Getting the plugins installed allow video to play, but if the file had audio libreoffice would hang when it came to play it, installing gstreamer1.0-pulseaudio fixed this.

Hope that helps someone :)

---

