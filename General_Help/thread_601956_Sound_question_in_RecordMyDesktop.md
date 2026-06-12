---
title: "Sound question in RecordMyDesktop"
date: 2007-11-03
forum: General Help
---

### Post by samurailink3 on 2007-11-03
I want to make gtk-recordmydesktop record any sound that is coming from alsa. Basically a loopback for audio. What would I put in the "Device" Section to accomplish this? I've tried using 'front', but the audio is very quite and almost fuzzy sounding. Using 'Default' just goes to my mic. Thanks!!

---

### Post by samurailink3 on 2007-11-04
Any way I could make the input feed back into the output (where the mic is supposed to be)?

---

### Post by philidox on 2008-02-25
Look at this post I fix my issue [http://ubuntuforums.org/showthread.php?p=4405489#post4405489](http://ubuntuforums.org/showthread.php?p=4405489#post4405489)

---

### Post by Crafty Kisses on 2008-02-25
> **philidox said:**
> Look at this post I fix my issue [http://ubuntuforums.org/showthread.php?p=4405489#post4405489](http://ubuntuforums.org/showthread.php?p=4405489#post4405489)

Install kmix.
```
sudo apt-get install kmix
```

---

