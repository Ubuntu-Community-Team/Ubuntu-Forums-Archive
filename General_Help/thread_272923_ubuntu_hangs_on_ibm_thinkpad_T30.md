---
title: "ubuntu hangs on ibm thinkpad T30"
date: 2006-10-07
forum: General Help
---

### Post by fafra33 on 2006-10-07
Dear Supporters,
I have a very annoying problem.

Time by time and apparently without any reason, my ubuntu completely hangs.

I can just power  off the computer and power on again.

A while ago I understood from different forums to change the theme from "human" to a different one; it's better, but this problem is here again.

Revision:
#uname -a
Linux enea 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Last "strange" logs i have:

#dmesg[17179633.144000] Bluetooth: RFCOMM TTY layer initialized
[17179662.588000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179662.588000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179662.588000] ide: failed opcode was: unknown
[17179701.312000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179701.312000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179701.312000] ide: failed opcode was: unknown

Thanks in advance
             F.

---

### Post by lawina on 2006-10-08
Your log mentions CRC errors. You might have have to do a disk check.

---

### Post by TheCan on 2006-10-10
Hi,

i had the same problem - it's related to the GPU, at least it worked for me with the fix i described here:

[http://www.ubuntuforums.org/showthread.php?t=274330&highlight=ibm+t30](http://www.ubuntuforums.org/showthread.php?t=274330&highlight=ibm+t30)

(allthough the thread is about another issue)

Please update this thread if it helps for you - i was suffering from this problem for over a half year :(

---

