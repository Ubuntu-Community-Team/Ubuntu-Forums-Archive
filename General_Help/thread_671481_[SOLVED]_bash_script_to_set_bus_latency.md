---
title: "[SOLVED] bash script to set bus latency"
date: 2008-01-18
forum: General Help
---

### Post by dannyboy79 on 2008-01-18
I want to set the latency of my sata and ide buses to 176 (hex b0) because I have been getting weird errors in my dmesg. I have a PVR-350. the errors state this: 
[ 6517.667012] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[ 6517.667018] ivtv0: Cause: the application is not reading fast enough.
[ 8310.996079] ivtv0: All encoder MPEG stream buffers are full. Dropping data.
[ 8310.996084] ivtv0: Cause: the application is not reading fast enough.

the latency for the PVR-350 per lspci -v is

00:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR-350
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at dc000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

when I read this here ([http://www.mythtv.org/wiki/index.php/PCI_Latency](http://www.mythtv.org/wiki/index.php/PCI_Latency)) about pci latency it doesn't say the same error I am getting but I thought I'd try this out and see if the dmesg errors go away.

This is the command I have to run to set the pci latency to 176

sudo setpci -v -s 00:0f.0 latency_timer=b0

can someone help me write this as a bash script that gets run when the computer turns on? I have also checked to make sure that the hard drives have DMA on.

---

### Post by dannyboy79 on 2008-01-22
found my own answer.

just added the lines of code to the /etc/rc.local file so that it looks like this before the exit 0

setpci -v -s 00:0f.0 latency_timer=b0
setpci -v -s 00:0f.1 latency_timer=b0

---

