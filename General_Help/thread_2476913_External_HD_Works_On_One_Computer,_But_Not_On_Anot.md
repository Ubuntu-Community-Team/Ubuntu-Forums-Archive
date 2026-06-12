---
title: "External HD Works On One Computer, But Not On Another"
date: 2022-07-11
forum: General Help
---

### Post by wpwend42 on 2022-07-11
I have an external hard drive I am trying to move a large set of files to another computer. Both run Ubuntu 18.04. My external hard drive works fine on the first one, but won't load on the second. I even tried it on a Windows laptop and it works fine. What could be causing this? I'd hate to have to do in smaller increments with a flash drive. 

Really frustrated in the past few years about how poor performance of external HDs has been for me with Ubuntu...

---

### Post by sudodus on 2022-07-11
- Please explain what you mean by 'won't load'. Does it mean that you cannot mount a partition and read or write files? Can you see the drive via **[FONT=Courier New]lsusb[/FONT]** or via **[FONT=Courier New]lsblk[/FONT]** ?

- Please check if the UEFI/BIOS system of the problematic computer can see the external hard disk drive.

- How is the power supply of the external drive, separate or via USB?

- Is some other external drive working well in the problematic computer? I guess from your opening post that a USB flash drive works well.

---

### Post by wpwend42 on 2022-07-11
1. Won't mount
2. It doesn't 
3. USB
4. Yep I have another one that mounts and flash drives do too. 

Thanks!

---

### Post by sudodus on 2022-07-11
When  the UEFI/BIOS system of the problematic computer can not see the external hard disk drive, you cannot expect that Ubuntu can see it.

When powered via USB it is possible that there is not enough power for it in this particular computer. One way to get around it is to connect the drive via a USB hub, that has external power supply.

Another solution might be to make one of the computers an ssh server (install the package openssh-server) and connect via a local network from the other computer. You can use **[FONT=Courier New]rsync[/FONT]** to copy the files from one computer to the other one.

---

### Post by Autodave on 2022-07-11
Sounds like the drive is asking for more power than what your power supply is capable of giving it.  I have had HDs do that in the past.....start drawing 2 or 3 times their specified draw.

Try disconnecting everything but the mouse and keyboard from your USB ports and then see if the PC will recognize it.  If it does, then you either need a new PS or new HD.

---

### Post by wpwend42 on 2022-07-11
oh a hub! I can try that...I have one of them around here somewhere...

Thanks everyone! I would have never thought about the power supply.

Edit: The one I have isn't a powered one...I can pick up a powered one at Target tomorrow.

---

### Post by wpwend42 on 2022-07-12
Okay I got a powered hub and a power supply for it, but new computer doesn't have a USB C port, so I ordered an adapter that will arrive tomorrow.

---

