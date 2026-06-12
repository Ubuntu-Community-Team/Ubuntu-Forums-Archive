---
title: "Alternate Sys Monitor"
date: 2013-07-01
forum: General Help
---

### Post by mayagrafix on 2013-07-01
Is there another way (or program) to monitor current processes and monitor system state (RAM, CPU usage, Network etc) other than System Monitor 3.8? I like to keep it on on one of my desktops to keep an eye on things, but lately when I start it one of the processors in my PC shoots up to a 100%, I remember this used to be some kind of bug in Ubuntu 8 a long time ago.

thanks 4 ur help :KS

---

### Post by tgalati4 on 2013-07-01
Open a terminal:

```
sudo apt-get install htop
man htop
htop
```

You can use *top* as well, but it is not as pretty.

---

