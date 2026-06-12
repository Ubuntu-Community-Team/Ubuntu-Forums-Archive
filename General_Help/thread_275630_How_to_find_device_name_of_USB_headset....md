---
title: "How to find device name of USB headset..."
date: 2006-10-11
forum: General Help
---

### Post by ModemMisuser on 2006-10-11
I've got 2 sound devices in my machine: an SB Audigy and a USB Headset.  I'm tyring to setup TeamSpeak to use the headset, but it requires the full /dev/filename devicename and I'm not sure how to determine what that is for the headset.  Any pointers appreciated... :)

---

### Post by Kateikyoushi on 2006-10-11
The dmesg command most likely lists it.

```
dmesg
```

---

### Post by ModemMisuser on 2006-10-11
O_o hmm, I will have to check.

---

### Post by ModemMisuser on 2006-10-11
I see no references to /dev files at all in dmesg output.

---

### Post by ModemMisuser on 2006-10-11
Wow, fast scrolling forums. :P

---

### Post by ModemMisuser on 2006-10-12
Still looking for the answer on this one.

---

### Post by viciouslime on 2006-10-12
Not sure how to get them all listed or anything, but have you tried /dev/dsp1

Works for me.

---

### Post by ModemMisuser on 2006-10-12
dsp1 seems to be the audigy card.

---

### Post by viciouslime on 2006-10-12
then try dsp0 that should be the other one, failing that you must have 3 cards and your headset must be dsp2...

---

