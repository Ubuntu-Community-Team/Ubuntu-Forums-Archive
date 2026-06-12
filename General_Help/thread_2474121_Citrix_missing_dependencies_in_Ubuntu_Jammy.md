---
title: "Citrix missing dependencies in Ubuntu Jammy"
date: 2022-04-22
forum: General Help
---

### Post by Herber on 2022-04-22
Help:
     I have used Citrix in Ubuntu since Ubuntu 13.04 with each new release.  With few problems.  I have traditionally used the tutorial    [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo).  Now the tutorial doesn't work.  I keep getting messages on attempt to install about missing dependencies.  I hope someone can help me.

---

### Post by mfior on 2022-04-23
Same problem. I have download the missing dependency from impish. [https://packages.ubuntu.com/impish/libidn11](https://packages.ubuntu.com/impish/libidn11). Citrix workspace now works

---

### Post by Herber on 2022-04-23
Thanks for the feedback I will give it a try.  Is that the only dependecy I will need?

---

### Post by mfior on 2022-04-24
I am not a citrix expert. i have to use citrix workspace to connect to my office pc. In my case the only dependency missing to install icaclient_22.3.0.24_amd64.deb was libidn11_1.33-3_amd64.deb. Bye[FONT=monospace][/FONT]

---

