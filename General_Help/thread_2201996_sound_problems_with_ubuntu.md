---
title: "sound problems with ubuntu"
date: 2014-01-26
forum: General Help
---

### Post by keith14 on 2014-01-26
Hi, ubuntu is installed  after win8. The audio is very broken-up if listening to something from utube I get bursts of sound and can not make out what is being said. Is this a general problem for people. Win8 audio is fine.
More information: the speakers on board laptop work ok except they are very small so I use a USB BT headset that doesn't work well at all.
I found the info below on line: I do use intel audio drivers is this the right thing to use? If so how will this get updated, I need to do something else?
sudo gedit /etc/modprobe.d/alsa-base.conf
add to file end:
options snd-hda-intel model=generic
Thanks,
Keith

---

### Post by keith14 on 2014-01-31
Hi,
 Without doing anything direct to resolve this the headset seems to work ok at the moment.
Keith

---

### Post by bc.haynes on 2014-01-31
Sounds like a loose connection. How do the on-board speakers sound now?

---

