---
title: "gutsy- black screen of death right after boot"
date: 2007-12-22
forum: General Help
---

### Post by nyx4826 on 2007-12-22
Hey guys, semi-newbie here. I upgraded to gutsy a few days ago on my inspiron 1420; have had a few problems with screen resolution since, but nothing major. Recently I tried to restart ubuntu as normal, and was faced with black screen of death rather than the login screen. Everything before that works normally-- booting, splash screen, etc. I can also still boot in recovery mode and get a usable root command prompt.

Help, please?

---

### Post by maddog39 on 2007-12-22
Sounds like an update screwed your Xorg configuration. Try this in recovery mode:
```

sudo dpkg-reconfigure xserver-xorg

```
It will give you a little text based wizard to reconfigure Xorg. Hope that helps.

---

### Post by inertz on 2007-12-22
Perhaps you can check on your monitor frequency setting.
Normally that cause this problem.

---

### Post by nyx4826 on 2007-12-22
maddog39, thanks for the help. I tried the configuration wizard you mentioned, but I'm not sure what driver to select for the nvidia GeForce graphics card. And after that point, I don't see a way to finish or exit the wizard without moving through a list of choices that I'm afraid will screw up other defaults. 

I also tried Xorg -configure, but this apparently had no effect either. Any more thoughts?

---

### Post by nynoah on 2007-12-26
use the Vessa driver to boot up.  Then later reconfigure your Xorg once you get it up and running

---

### Post by jadymitchell on 2007-12-28
I have the same problem, as mentioned in [this thread ]("http://ubuntuforums.org/showthread.php?t=647276&goto=newpost").  Would love to find a solution!

---

### Post by jken146 on 2007-12-28
The **nv** driver is usually the safe bet, unless you have already installed the nvidia driver (restricted drivers manager), in which case you can pick nvidia if you like.  The important thing is to pick resolutions and refresh rates that your monitor is capable of.

---

