---
title: "Setting python to run with lower priority"
date: 2007-04-02
forum: General Help
---

### Post by mgchan on 2007-04-02
On my server I have torrentflux installed, however it also serves up video and sometimes transcodes video on the fly (TivoDotNet).  The CPU is not very quick (Athlon XP 1600+) so if I have a torrent going at the same time as I'm trying to watch video, it tends to lag.  Is there a way to get bittornado to launch in a lower priority? (or alternatively, ffmpeg to run at a higher priority, though I'd prefer the former)

---

### Post by spin2cool on 2007-04-02
You probably want to look into the "renice" command.

---

