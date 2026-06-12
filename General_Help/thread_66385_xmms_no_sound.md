---
title: "xmms no sound"
date: 2005-09-17
forum: General Help
---

### Post by bam on 2005-09-17
installed xmms and have no sound, it plays but I hear nothing, alsamixer is turned up, any ideas?

---

### Post by palsyboy on 2005-09-17
When running XMMS, hit Ctrl+P.  Under the "Audio I/O Plugins" tab, do you have the correct output plugin?  Most commonly you will want an ALSA plugin.

Also, if you're playing something such as a FLAC, you may need to get the proper  input plugin.

---

### Post by Perfect Storm on 2005-09-17
This could also be the problem: Find CD audio player Input plugin (under audio I/O plugins) and configure it to digital instead of analog.

---

