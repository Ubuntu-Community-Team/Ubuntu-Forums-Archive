---
title: "Libtheora (??) issues"
date: 2007-12-13
forum: General Help
---

### Post by bluemike807 on 2007-12-13
Hi, Im having a nonspecific problem - certain media players, mplayer and vlc in particular, will not open, quoting this error:

mplayer: error while loading shared libraries: /usr/lib/libtheora.so.0: invalid ELF header

Also, when I do a regular sudo apt-get upgrade, it mentions..: something similar - that the same file does not have the 'magical' ELF header, or somesuch (I dont seem to be able to reproduce it as it only displays the message (three times) when there is an actual upgrade for my system, presently there isnt.

**EDIT** here is a paste of the error when updating.

ldconfig: /usr/lib/libtheora.so.0: is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libtheora.so.0.2.0 is not an ELF file - it has the wrong magic bytes at the start.

ldconfig: /usr/lib/libtheora.so.0 is not an ELF file - it has the wrong magic bytes at the start.



I've googled the error(s) and found nothing... how do I fix it so that they go away and I can use these players?

Thanks

---

### Post by bluemike807 on 2008-01-07
Bump! Can someone please help me with this issue? its not going away - I've since upgraded my distribution to Gutsy (without reinstall) and its still plaguing me.

---

