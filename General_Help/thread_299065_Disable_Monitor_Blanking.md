---
title: "Disable Monitor Blanking"
date: 2006-11-13
forum: General Help
---

### Post by MikeyD on 2006-11-13
How do I disable the monitor blanking that occurs after the computer is idle?

I already turned off the screen saver and the BIOS does not have an option to turn off any power management features. How can I disable this blanking? I want the monitor on at all times.

Thanks in advance for any help.

---

### Post by Ramses de Norre on 2006-11-13
Remove the DPMS option in the Monitor section of your xorg.conf.

---

### Post by MikeyD on 2006-11-13
I removed it but it is still doing it. I rebooted to make sure the changes took effect, but it still blanks. Any other ideas?

---

### Post by lolikapuxa on 2006-11-21
same here. 

 this is freaking me out!

---

### Post by James79 on 2006-12-01
I've tried google'ing this "problem", and many people seem to recommend setterm. Something along the lines of:

```
setterm -powersave off -blank 0
```

For me this doesn't work, it returns "cannot (un)set powersave mode".

Apparently this is most likely caused because you've issued the command from within X, problem is I don't even have X installed. This is a GUI'less server I have, which is typically just sitting at the login prompt.

---

### Post by James79 on 2006-12-01
Actually I just found [this thread]("http://www.ubuntuforums.org/showthread.php?t=41788&highlight=disable+screen+blanking"). Sounds like he's got a good answer.

I've executed the commannd remotely (ssh), I'll know if it works when I get home tonight.

---

