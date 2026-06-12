---
title: "Please Help Uninstall Broadwave"
date: 2008-01-11
forum: General Help
---

### Post by TekNullOG on 2008-01-11
I saw a Google ad promoting **BroadWave,** an audio streaming software program designed to broadcast any audio connected to the sound input on the PC.

I was tempted to try it due to the few sofwares available under linux that do this.

Well, I don't like it but** I can't seem to uninstall it**. It even starts every time Ubuntu loads. (even once removing the option in the software) It is not listed under System>Administration>Services

Has anyone tried this software and more importantly, **does anyone know how to remove it?**

---

### Post by TekNullOG on 2008-01-14
I feel kinda dumb but I found the solution. I searched for broadwave on my computer and found /opt/nch/broadwave/

Inside this, there is a bin folder with a uninstall.sh file. Run it in a terminal and it should remove itself.

Hope this helps someone else in the future.

---

