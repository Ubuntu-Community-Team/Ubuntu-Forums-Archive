---
title: "Help with Crazy Error!"
date: 2006-10-28
forum: General Help
---

### Post by buddhagui on 2006-10-28
Everytime I install new software or even when I write my own code and compile it (I write software) I am getting this message:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Then it goes on link normal. Can someone please help me get rid of this?

Thank you,
chris

---

### Post by ansi on 2006-10-28
> **buddhagui said:**
> Everytime I install new software or even when I write my own code and compile it (I write software) I am getting this message:

It isn't a crazy error. See your /etc/X11/xorg.conf about sections "InputDevice" and comment out nosuch devices. And don't forget to restart X's, after.

---

