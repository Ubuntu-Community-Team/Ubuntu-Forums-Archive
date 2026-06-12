---
title: "sound preferences"
date: 2008-05-17
forum: General Help
---

### Post by sabbs666 on 2008-05-17
New to Linux and enjoying Ubuntu.

However, strange problem with sound preferences i.e. no sound generally but on the occasional boot up I have sound. Firefox also a problem no sound.  No problems with media playback using Rhythmbox?

Any suggestions would be appreciated.

Had not selected the correct playback device as default in PulseAudio Device Chooser - Hence no sound events!

---

### Post by strabes on 2008-05-17
Please open a terminal window (Applications > Accessories > Terminal), run the following command, and paste its output in this thread. ```
lspci |grep audio -i
```

---

### Post by sabbs666 on 2008-05-17
Thanks strabes

Output from terminal as follow's;

******-desktop:~$ lspci |grep audio -i
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

---

### Post by sabbs666 on 2008-05-19
Had not selected the correct playback device as default in PulseAudio Device Chooser - Hence no sound events!

---

