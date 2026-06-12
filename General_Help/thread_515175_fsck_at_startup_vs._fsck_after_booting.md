---
title: "fsck at startup vs. fsck after booting"
date: 2007-08-01
forum: General Help
---

### Post by DJTurboToJo on 2007-08-01
Hi,

I dont have an issue with fsck checking my harddrive and it's also not too long. My question is:

Why does the fsck run during startup (after 30 mounts) takes much longer than the fsck run that I can execute via a terminal?

I mean  when my system starts, the check takes roughly 30s. Whereas the command:
```
fsck /dev/sda5
```
takes only 1s.

What is the difference in these two methods?

EDIT: I just saw that fsck checks my sda5 at every startup and this is as fast as in the terminal, but only after 30 mounts comes fsck with a status bar which then takes a bit longer. So what does fsck do differently then?


Thanks,
TurboToJo

---

### Post by be4truth on 2007-08-02
It is a bad idea to check a file system that is already mounted. It is protected by the operating system. If you do so you risk to damage it. It is as if a surgeon operates him/herself !
At startup all there is, sits in the RAM and your root file system not mounted, means not hot. You can check it safely.

---

### Post by DJTurboToJo on 2007-08-02
Thanks for your answer...although that wasnt really my question.

I know that you shouldnt run fsck on a mounted system so I did start with a Live CD and let it run   then.

My problem is that I dont know why fsck during the startup takes so much  longer and also shows a stauts bar. Whereas when I start fsck in a terminal it takes only 1s and then comes the message about blocks and so on. So I thought that fsck during the startup checks something else than just the usual command, maybe with some options...I dont know.

TurboToJo

---

### Post by be4truth on 2007-08-02
Does it really take only 1s ?. I can't imagine that,  say a 50 GB root partition,  takes only 1 s to be checked. I would be suspicious if that happens. But one never knows....

---

### Post by DJTurboToJo on 2007-08-02
My ubuntu isnt 50GB its only 5GB ;).

However, isnt it weird that it runs so fast. Maybe I have to call fsck with some options? Maybe I ll study the man pages.

Anyway thanks,
TurboToJo

---

