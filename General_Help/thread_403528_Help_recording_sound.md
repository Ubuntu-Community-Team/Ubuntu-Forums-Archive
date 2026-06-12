---
title: "Help recording sound"
date: 2007-04-07
forum: General Help
---

### Post by ThaDoctor99 on 2007-04-07
Hi 

I can't record any sound on my computer have tried with different programs audicity returns that I should look up whether I have a mic connected or something, but I have that connected
What could the problem be? 

Should I mount it first ?

---

### Post by heimo on 2007-04-07
Check (in Audacity) Edit->Preferences->Audio I/O->Recording Device, try different devices if unsure. Also run alsamixer on command line to make sure your mic is not muted and it's selected as an input source.

---

### Post by garybrlow on 2007-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This currently a bug in the ALSA package. Mainly in feisty but Dapper/Edgy may have been updated using the same version so its related. Read, review, confirm here [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531). Please register if you haven't already done so in order to post/confirm and report bugs to help make ubuntu better.

Cheer!!!

GaryBrlow :biggrin:

---

### Post by ThaDoctor99 on 2007-04-07
Think it works now no sound on Mic...

---

