---
title: "Sound Stopped Working"
date: 2013-02-11
forum: General Help
---

### Post by Arkaman on 2013-02-11
Hello, my sound has stopped working.  I am running Ubuntu 12.04.  I have done all my updates.  All I see in my sound control panel is SPDIF.  This is on a Dell Precision M65.  The only thing that works is the headphones.  If I plug in the headphones I can hear audio, but nothing through the built in speakers.  If you need more info just ask.  Thanks.

---

### Post by Impavidus on 2013-02-11
Has the sound been muted? Try alsamixer and/or pulse audio controller (in a terminal: **alsamixer** and **pavucontrol**). I've noticed they can independently mute the sound, although there is some communication between the two. Very confusing.

---

### Post by Arkaman on 2013-02-13
> **Impavidus said:**
> Has the sound been muted? Try alsamixer and/or pulse audio controller (in a terminal: **alsamixer** and **pavucontrol**). I've noticed they can independently mute the sound, although there is some communication between the two. Very confusing.

Alsamixer is not muted.  Pavucontrol does not seem to be on the computer.  Also I already checked the Sound Control Panel it is not muted.  Like I said I can hear stuff if I plug a set of headphones in, but the normal internal speakers are no longer listed.  Instead the only thing listed is SPDIF.  Which this laptop does not have. :confused:

---

### Post by Yellow Pasque on 2013-02-13
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1036004](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1036004)

---

### Post by Arkaman on 2013-02-13
> **Temüjin said:**
> [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1036004](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1036004)

Thankyou, your link lead me to this link.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232/comments/32)
Which fixed my issue.  :popcorn:

---

