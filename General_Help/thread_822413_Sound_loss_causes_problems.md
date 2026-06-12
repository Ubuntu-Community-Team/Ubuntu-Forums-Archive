---
title: "Sound loss causes problems"
date: 2008-06-08
forum: General Help
---

### Post by Ragzouken on 2008-06-08
I can't use sound in both firefox and rhythm box at the same time. I can open rhythm box and play music, but if I want sound in firefox I must close rhythm box first. After doing that, if I close firefox, everything goes crazy, I can't get sound in rhythm box, I can't reopen firefox, terminals start to freeze and prompt force-quit which never works. I can't even get the window up to reboot the computer. So I use ctrl-alt-backspace, the standard sound is absent, I then reboot and all is well until I repeat the process. Any idea what causes these sound-denying actions to have such drastic effects on non-sound related things? Is it possible to fix?

---

### Post by leandropls on 2008-06-22
I have the same problem, but not using firefox. I just found out that this is a fault on pulseaudio.

I tried restarting my session using control-alt-backspace, but I couldn't loggin again although gdm had started normally.

Thru console (tty1) I found out that all my apps were still running and I killed one by one until I could loggin again.

So, what app was responsible for that? pulseaudio.

I don't know what to say in a bug report about that, though. But I think it should be marked with highest priority (since it makes the whole graphical interface freeze for so little).

---

### Post by Happy_Man on 2008-06-22
There's a guide with how to fix this stuff at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by iaculallad on 2008-06-22
> **leandropls said:**
> I have the same problem, but not using firefox. I just found out that this is a fault on pulseaudio.

I tried restarting my session using control-alt-backspace, but I couldn't loggin again although gdm had started normally.

Thru console (tty1) I found out that all my apps were still running and I killed one by one until I could loggin again.

So, what app was responsible for that? pulseaudio.

I don't know what to say in a bug report about that, though. But I think it should be marked with highest priority (since it makes the whole graphical interface freeze for so little).

Install the audio support wrapper:

```
sudo apt-get install libflashsupport
```

---

