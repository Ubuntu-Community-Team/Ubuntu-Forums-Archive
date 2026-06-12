---
title: "System sound lost when using virtualbox"
date: 2007-10-03
forum: General Help
---

### Post by D_dog on 2007-10-03
I recently installed virtualbox and configured it using the oss sound adapter. My installation of the guest OS went off without a hitch (Windoze XP) The problem is when I have the guest OS up and running I do not have any sound on my system. I was unable to play system sounds or ogg files nothing would play. The guest OS sound worked fine. When I exited from virtualbox my system sound came back and works as usual.

Where can I look to solve this problem. I am sure its a setting somewhere. I am using an ASUS P5B motherboard and the onboard sound system.

Thank you all in advance.

---

### Post by swisscow on 2007-10-03
try the alsa option in the settings - worked for me

---

### Post by jocko on 2007-10-03
You can't get sound from alsa and oss at the same time. Change virtualbox to use alsa instead.

---

