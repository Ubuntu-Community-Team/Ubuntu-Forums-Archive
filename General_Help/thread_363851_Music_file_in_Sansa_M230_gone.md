---
title: "Music file in Sansa M230 gone"
date: 2007-02-17
forum: General Help
---

### Post by VigilanteNighthawk on 2007-02-17
I've been using Ubuntu for a few months now, and I'm really liking it.  One of the biggest issues I'm having is that when I mount my Sansa m230 mp3 player,  it won't show the music folder or any of the music in that folder.  This occurs both under auto detect and msc mode in linux, and it occurs in MSC mode in windows as well.  I'm not quite sure what to do to fix this problem, as I have not found any similar problems on the ubuntu forums.  

Thanks

---

### Post by VigilanteNighthawk on 2007-02-17
Found the problem.  The sansa mp3 players use a different directory structure under MSC mode than it does under MTP mode.  The files that were missing were installed in windows under MTP mode into the Music directory.  I've removed the files and reinstalled them under audible in MSC mode.

---

