---
title: "Sound Problem"
date: 2007-02-06
forum: General Help
---

### Post by Consumed on 2007-02-06
I've been having sound issues with Ubuntu Edgy x64.  I know it worked first when I installed it.  Then after it stopped working I was able to find a previous post which I cannot find anymore.  It detailed how to blacklist a certain modem driver from being listed which he said can cause some sound conflicts.  Worked for a while after that.  So this time I went to the /etc/modprobe.d/modems and uncommented to block all of those.  Rebooted, still nothing.  I've checked alsamixer and my General->Pref->Sound settings.  Does anyone know what problem I am referring to?  It could be also a diff problem, any other ideas?  I have an Intel ICH integrated sound card if that helps.

---

### Post by comfurtn on 2007-02-06
Well, there's not much help I can offer you without some additional information...

What is the exact model/chipset of your sound card?  AND, what is the output of:
> lsmod ?

---

### Post by r4ik on 2007-02-06
Try,

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+Audio](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+Audio)

Good luck !

---

