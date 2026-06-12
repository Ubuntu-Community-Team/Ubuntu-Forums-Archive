---
title: "Elantech Touchpad - Stops moving with multiple touches?"
date: 2013-05-12
forum: General Help
---

### Post by blind3d on 2013-05-12
I have the ASUS k55n on Ubuntu 12.10 64 bit, and I think might be something to do with the gestures.

**The problem:** The mouse buttons and touchpad are built in together as one. If I have my thumb resting on the left mouse button, the pointer won't move after that. 

Infact I cannot have 2 fingers on the touchpad at all, the cursor just won't move. Not even old style, where you could flip the cursor back and fourth by having two fingers on the touchpad.

 I think this has something to do with the gestures engine. I am not sure. 
If I could disable gestures to get this to work I wouldn't mind, as long as I have the scroll feature that currently works. 

I looked at my manufacturer specs , it appears I am on a elantech touchpad. 
dmesg checks out and shows elantech drivers loaded

```

derpington@derpington:~$ dmesg | grep -A4 elantech
[   18.993257] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   19.004968] psmouse serio1: elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.
[   19.128991] r8169 0000:05:00.0: eth0: link down
[   19.129028] r8169 0000:05:00.0: eth0: link down
[   19.136990] init: alsa-restore main process (1019) terminated with status 19
[   19.150131] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8

```

Is there a way I can maybe change the bounds of the touchpad, to not include the button area?
Maybe I could disable gestures and get this to work, but I really would like to have the mouse scroll, which seems not so much as a 'gesture'.

---

### Post by samcoinc on 2013-08-30
I have an asus k55a.
I am having the same issue.  I set the AreaBottomEdge to 1800 which works well to make the buttons a dead area.

Same issue though - even though the lower part of the mouse pad is dead - I cannot rest my thumb on the left mouse button as it stops the pointer from moving. 

I have spent a good part of a day looking for a solution but have found none.

thanks
sam

---

