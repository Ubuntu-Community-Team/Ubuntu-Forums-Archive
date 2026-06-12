---
title: "apt-mark unhold not removing hold"
date: 2013-09-16
forum: General Help
---

### Post by Nick Payne on 2013-09-16
I had a couple of packages (acroread and xpdf) on which I had used apt-mark hold to prevent them being upgraded. I eventually decided that I could upgrade acroread, and used apt-mark unhold to remove the hold on acroread. However, after removing the hold, I still can't upgrade acroread with apt-get upgrade. Below is the output from running the commands in terminal. Ubuntu 13.04 amd64.

```
nick@nick-desktop ~/lilypond $ sudo apt-mark unhold acroread
Cancelled hold on acroread.
nick@nick-desktop ~/lilypond $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  acroread xpdf
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded
```
I found I could perform the upgrade in Synaptic successfully. Any ideas why removing the hold didn't work on the command line.

---

### Post by oldos2er on 2013-09-16
Maybe you needed to use **sudo apt-get dist-upgrade**, which is equivalent to Synaptic's smart upgrade.

---

