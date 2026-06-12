---
title: "no audio"
date: 2008-01-24
forum: General Help
---

### Post by bmesta on 2008-01-24
I cant hear any audio at all. Its driving me insane. can someone help me fix this?

---

### Post by Metaljaz on 2008-01-24
right click on the volume control on the top right corner of the screen. Select open volume control and make sure that the PCM and Master are not muted.

If this doesn't help tell us a little:
Is this a fresh install? What version of Ubuntu are you using? What sound card do you have?

---

### Post by bmesta on 2008-01-24
I already check that. thats my audio card Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01). I think its built-in thou. and yes it is a fresh install of Ubuntu 7.10 I been tryin to solve this problem for a why...

---

### Post by Metaljaz on 2008-01-24
try right clicking on the volume control button again. Select preferences and make sure that  the intel Ich (Alsa Mixer) family is selected. Then select PCM.

If this doesn't work try this wiki:

[http://alsa.opensrc.org/index.php/FAQ#How_can_I_check_whether_ALSA_works.3F](http://alsa.opensrc.org/index.php/FAQ#How_can_I_check_whether_ALSA_works.3F)

Should find a solution here. Follow the wiki and check to make sure alsa is working first.

---

### Post by Casual Fan on 2008-01-24
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

