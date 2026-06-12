---
title: "what do you thing about this brainstorm idea?"
date: 2008-07-10
forum: General Help
---

### Post by eldragon on 2008-07-10
[http://brainstorm.ubuntu.com/idea/10979/](http://brainstorm.ubuntu.com/idea/10979/)

i posted since it came from my own frustrating experience. would like to hear some input on it.

---

### Post by DarinB on 2008-07-10
May be stupid to say but is it possible that black listing will nix the install if the problem with the module can be corrected and is necessary ?????

---

### Post by konungursvia on 2008-07-10
What would stop it from blacklisting things that require mobile plug-and-play hardware which is sometimes present?

---

### Post by eldragon on 2008-07-10
as far as i know (and it usually isnt much)...needed code is included IN the kernel. and modules would add functionality to hardware.

example;
during the gutsy install, the 8139too and the sdhci modules blocked me from booting my install.

i used the alternate cd to install, and right after the very first boot the computer would freeze completely, and thus needing to do some manual module deleting during the alternate install in order to be able to boot the first time AND blacklist the offending modules.

blacklisting them will render some harware useless, but at least you get a working computer to work with and debug the problem.

---

### Post by eldragon on 2008-07-10
> **konungursvia said:**
> What would stop it from blacklisting things that require mobile plug-and-play hardware which is sometimes present?


a failed modprobing isnt one that doesnt find hardware. its one that doesnt exit gracefully. in fact, my idea should work only when modprobing doesnt return at all....

---

