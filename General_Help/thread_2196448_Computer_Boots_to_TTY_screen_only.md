---
title: "Computer Boots to TTY screen only"
date: 2013-12-29
forum: General Help
---

### Post by SuperFreak on 2013-12-29
A friend has an older HP Pavillion desktop that I installed 12.04 on(it's now at 12.04.3). It has worked quite well for him for some time. Recently the kernel upgraded and now boots to the tty screen and no graphics. I tried recovery mode in low graphics but it didn't help(still booted to tty). I tried repairing broken packages and boot repair to no avail. From the web I saw editing the grub file and changing quiet splash to quiet splash nomodeset or just nomodeset might work but it didn't work.
The computer will boot to graphics mode using an earlier kernel but this seems to me to be a stop gap solution. Any suggestions would be welcomed.

---

### Post by steeldriver on 2013-12-29
Can you provide some info about the graphics device (brand - model if possible)?

---

### Post by SuperFreak on 2013-12-29
Thanks Steel Driver. I will get that info the next time I'm over at my friend's (tomorrow morning I hope). I think it is onboard Nvidia

---

### Post by steeldriver on 2013-12-29
several people are having issues with recent nvidia upgrades - if that is the case here, these instructions may help --> [http://askubuntu.com/a/396159/178692](http://askubuntu.com/a/396159/178692)

---

### Post by SuperFreak on 2013-12-29
Thanks Steeldriver that is certainly worth trying

---

### Post by SuperFreak on 2013-12-30
> **steeldriver said:**
> several people are having issues with recent nvidia upgrades - if that is the case here, these instructions may help --> [http://askubuntu.com/a/396159/178692](http://askubuntu.com/a/396159/178692)


Worked perfectly. Thanks

---

### Post by steeldriver on 2013-12-30
Happy to help - please consider marking the thread as [SOLVED] using the 'Thread Tools' menu at the top of the thread

Ironically my own nvidia-based laptop broke after updating this morning... and so far jockey-text hasn't worked for me :mad:

---

### Post by SuperFreak on 2014-01-01
Reopened this thread because another, related problem popped up. While the issue with graphics is now working properly on boot I now have a new problem with the computer not shutting down. On shutdown it appears that Ubuntu shuts down as the screen is blank but the power button on the computer remains lit. Are these issues, including the original issue with boot to tty screen resolved in 13.10 Xubuntu. The reason I ask is the issues all seem to be connected with NVidia driver updates and if installing 13.10 will resolve things I may do that for my friend. Sorry to resurrect this thread but the problems seem connected

---

