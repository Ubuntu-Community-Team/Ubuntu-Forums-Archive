---
title: "RealPlayer 10 does not start"
date: 2005-05-20
forum: General Help
---

### Post by bruizer on 2005-05-20
I have been using RealPlayer 10 on Hoary for about 3 months now, and all of a sudden it just doesn't even start. I try running from term to see the errors, and nothing comes up, just sits there spinning it's wheels. I check /var/logs/messages and nothing shows up there either.

After I try running RealPLayer, and watch it hang, I "ps -A | grep realplay" and see something like this:
10630 pts/0    00:00:00 realplay
10635 pts/0    00:00:00 realplay.bin
10637 pts/0    00:00:00 realplay.bin
10638 pts/0    00:00:00 realplay.bin

The bin files tell me it is trying to start but I am getting no other info. Anyopne seen this before or know how I can clear it?

---

### Post by NeoChaosX on 2005-05-20
If you have the ESD sound system running, RealPlayer has conflicts with it. You can either do "killall esd" in the console before running Real or follow steps 4 and 5 in [these](http://ubuntuforums.org/showpost.php?p=80282&postcount=21) instructions.

---

### Post by Xian on 2005-05-20
[QUOTE=bruizer]The bin files tell me it is trying to start but I am getting no other info. Anyopne seen this before or know how I can clear it?[/QUOTE]
If you're talking about an out of the blue occurrence, then yeah I've seen it do this on my box, and even if I kill the running processes it still will not start properly until the next reboot. I can only assume some type of sound conflict but I've never managed to localize what might be the cause.

If it is more persistent then I'd have a look at the ESD daemon.

---

### Post by bored2k on 2005-05-20
. Disable the sound server.
. Use alsa instead of esd.

---

### Post by bruizer on 2005-05-20
ALSA kills XMMS and ESD kills RealPlayer... Anyone have any suggestions how to get around this one?

---

### Post by bruizer on 2005-05-20
I justed killed ESD daemon and RealPlayer setup kicked right up! Thanks guys!

---

### Post by bored2k on 2005-05-20
[QUOTE=bruizer]ALSA kills XMMS and ESD kills RealPlayer... Anyone have any suggestions how to get around this one?[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd+gandalf](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd+gandalf)

---

### Post by bruizer on 2005-05-20
Thanks bored2k... that link got everything working as desired.

---

