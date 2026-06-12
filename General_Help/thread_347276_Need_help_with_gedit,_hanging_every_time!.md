---
title: "Need help with gedit, hanging every time!"
date: 2007-01-27
forum: General Help
---

### Post by stephentyler20 on 2007-01-27
While trying (Again) to configure my bluetooth tonight, I noticed that the usual "gksudo gedit /etc/bluetooth/hcid.conf" command causes the text editor to open, but then it hangs and doesn't show anything for a minute or two. I can either force quit, or wait for the editor to finally open, which is a huge pain. 

Is there any fix for this? It's extremely annoying, and makes adjusting things very difficult. I'm running Ubuntu 6.10, and I'm fairly new at this so go easy! (But I have done several searches, and not turned up anything useful).

---

### Post by taurus on 2007-01-27
```
sudo nano -Bw /etc/bluetooth/hcid.conf
```
<Ctrl>x to exit and Y to save it.

---

### Post by stephentyler20 on 2007-01-27
That does work, but is there any way to bring back gedit? It just doesn't seem right... the hang is actually more like 4 or 5 minutes, totally unacceptable. Thanks for the reply...

---

