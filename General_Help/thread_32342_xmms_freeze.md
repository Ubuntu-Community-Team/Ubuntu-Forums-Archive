---
title: "xmms freeze"
date: 2005-05-07
forum: General Help
---

### Post by hrvoje-pula on 2005-05-07
hi,
i have a problem with my xmms.

when I put a song in it just freeze. no sound no nothing. what can I do. I 've tried to reinstal it but nothing.

---

### Post by Gandalf on 2005-05-07
[QUOTE=hrvoje-pula]hi,
i have a problem with my xmms.

when I put a song in it just freeze. no sound no nothing. what can I do. I 've tried to reinstal it but nothing.[/QUOTE]
 go to preferences of XMMS and select Esound/ESD as audio output, don't select ALSA neither OSS

---

### Post by Kino on 2005-05-08
I had also the same problem. Can you explain a little bit the difference between alsa, esd and OSS?, how are they intended for?, and the purpose of having so many different Sound subsystems.

The only thing I know is that OSS is the "old" sound system in Linux, Alsa is supossed to replace OSS and ESD is the specific GNOME sound server system.Am I right?

Thank!

---

### Post by hrvoje-pula on 2005-05-08
Thanx. it's ok now.

---

### Post by Gandalf on 2005-05-08
OSS, Alsa and ESD are different sound servers, ubuntu use ESD by default but you can [enable alsa](http://ubuntuforums.org/showthread.php?t=32063)

---

