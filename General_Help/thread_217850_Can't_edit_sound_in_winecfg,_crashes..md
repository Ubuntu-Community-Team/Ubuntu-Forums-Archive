---
title: "Can't edit sound in winecfg, crashes."
date: 2006-07-17
forum: General Help
---

### Post by Poka64 on 2006-07-17
well, I'm trying change to the tab in winecfg, but when I try to do that I'm getting this error:

```
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/peter/.kde/socket-razor.
can't create mcop directory

```

Got the same faultmessage when I tried to run Neverwinter nights :(

Is there a way to manually edit the config files ?

---

### Post by Thenotsowyzewun on 2006-07-17
Remove this file from the Shared Object Library Files: winearts.drv.so - ```
rm /usr/lib/wine/winearts.drv.so
``` should do the trick.

You might want to make a backup incase it doesn't work.

Tell us how you get on :)

---

### Post by Poka64 on 2006-07-17
Solved the crash issue atleast with the help of this page: [http://www.ubuntuforums.org/showthread.php?t=196033](http://www.ubuntuforums.org/showthread.php?t=196033)

*Doing a mkdir /tmp/ksocket-stephen (stephen = my username) solved it.*

---

