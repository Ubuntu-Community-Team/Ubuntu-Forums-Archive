---
title: "Moving Ubuntu system to new laptop"
date: 2017-01-03
forum: General Help
---

### Post by petervkay on 2017-01-03
I'm currently running Ubuntu 16.04 on an ASUS X551 which is starting to slow down considerably.  I'd like to get a laptop that I can travel with, something lightweight and compact with a little bit more power.  Ideally, I'd like to be able to transfer my entire Ubuntu system over (I'm a web developer and would rather not reinstall my development environment).  A few questions 1) Does anyone have a laptop recommendation? 2) I was looking at a Dell xps 13. From what I've read Ubuntu 14.04 works best on it and people have had mixed results with 16.04.  Is there a way to downgrade my Ubuntu version on my current installation to 14.04 without messing up my development environment too much?

I'm a moderate Ubuntu user, pretty comfortable doing what I need to do, but don't understand much about how Ubuntu actually works.

---

### Post by ian-weisser on 2017-01-03
> **petervkay said:**
> Is there a way to downgrade my Ubuntu version on my current installation to 14.04 without messing up my development environment too much?

Seems unlikely. The OS isn't a black box. Most dev environments that I see are tightly bound to the OS version.

I would be curious why your current system is becoming less responsive. An hour using simple tools (htop, syslog, etc) and a bit of shell-fu might cure your problem.

---

### Post by Keith_Helms on 2017-01-03
There's the operating system itself with all its settings and there's your personal data and config files.  Unless you're cloning to the exact same hardware, you can't just move the operating system and expect it to run with no glitches.

As far as your development environment, your settings should be saved in config files or a database somewhere.  Moving to a new machine should just be a matter of installing the software and then copying the configuration data so that you don't have to reconfigure from scratch.  For example, I use Eclipse for java development and I mostly just have to copy my workspace directory to a new machine to get up and running there.

---

