---
title: "Sound Stop working"
date: 2013-12-11
forum: General Help
---

### Post by lumaja2 on 2013-12-11
Ubuntu 12.04 precise  Sound stop working, Test sound does not work, it was working before. What should I do. Thank you

---

### Post by Kirboosy on 2013-12-11
I had a similar problem with my computer and I fixed it doing the following.

```
sudo alsa force-reload
```

Reboot the computer after command finishes

Check to see if the sound started working. If not open up the sound panel and see if it even detects a sound card. 

Hope that helps!
~Caboose
PS I moved the volume levels in my control panel after the reboot and that is when the sound finally started working. Hopefully you have a similar experience.

---

