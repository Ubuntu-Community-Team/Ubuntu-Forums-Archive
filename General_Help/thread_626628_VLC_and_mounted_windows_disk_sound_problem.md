---
title: "VLC and mounted windows disk sound problem"
date: 2007-11-29
forum: General Help
---

### Post by zeller on 2007-11-29
Using VLC I clicked on "Open Directory..." in the drop down menu, found my mounted Windows partition, and opened the appropriate directory for my DVD files. The VIDEO_TS folder holding all the .vobs and .ifos for The Fountain.

VLC played the DVD beautifully, just like normal.

Then I clicked on the "X" to close VLC while the movie was still playing. Interesting result: The application closed ok, but the audio was still playing.

Ok, so I opened VLC once again and tried it a second time. It did the same thing again, leaving me with two audio outputs that were 20 minutes apart. They played at the same time, overlapping. It was interesting for only a minute.

Anyone know how to fix this? A quick logout and login is my only workaround currently since it stops all processes.

Also, might it have something to do with reading the DVD files from an NTFS partition instead of Linux's own partition?

---

### Post by tech9 on 2007-11-29
> **zeller said:**
> Using VLC I clicked on "Open Directory..." in the drop down menu, found my mounted Windows partition, and opened the appropriate directory for my DVD files. The VIDEO_TS folder holding all the .vobs and .ifos for The Fountain.

VLC played the DVD beautifully, just like normal.

Then I clicked on the "X" to close VLC while the movie was still playing. Interesting result: The application closed ok, but the audio was still playing.

Ok, so I opened VLC once again and tried it a second time. It did the same thing again, leaving me with two audio outputs that were 20 minutes apart. They played at the same time, overlapping. It was interesting for only a minute.

Anyone know how to fix this? A quick logout and login is my only workaround currently since it stops all processes.

Also, might it have something to do with reading the DVD files from an NTFS partition instead of Linux's own partition?

maybe look at the processes and kill vlc if it is still running after you close it down

---

