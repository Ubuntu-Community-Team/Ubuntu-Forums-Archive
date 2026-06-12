---
title: "Virtualbox steals sound"
date: 2008-05-09
forum: General Help
---

### Post by HokeyFry on 2008-05-09
VirtualBox has a bad habit of making my Ubuntu sound stop working when it's running. I have it using OSS, and Ubuntu should be using ALSA, but I've tried it vice versa as well and I still can't figure out why my sound stops working when the VM is open. The VM sound works fine, and when I stop the VM from running, I get my sound back again. It is also worth noting that this is not an issue when I tell the VM to use the null audio driver rather than OSS or ALSA.

---

### Post by markharding557 on 2008-05-09
disable the sound driver in virtualbox unless you explicitly need it

---

### Post by HokeyFry on 2008-05-09
I do need the sound driver. I am running our University XP image on it and it needs all of the functionality of Windows so I can easily troubleshoot it. That is why having sound is a must. I just don't want to have to play music via the VM, and there are noise alerts I would like to have. I haven't had this issue before Hardy, and I don't see why if it's using OSS why it would affect ALSA, and vice versa, because normally I can have multiple applications running using both and I don't have this problem.

---

