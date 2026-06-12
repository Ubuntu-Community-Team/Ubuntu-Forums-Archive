---
title: "Partition help please"
date: 2014-01-20
forum: General Help
---

### Post by sports fan Matt on 2014-01-20
I created roughly a 10 GB partition for Ubuntu just to get refamiliar with it when I get my own system back from the repair shop.  I can see the Windows partition (SDA2) but since I deleted the allocated space that went to the space I used for Ubuntu, I can no longer boot into W7.  There is a text file that can be run either from GParted or not that sees my partitionsas I recall., but I cannot remember which it is.  Can someone please help me be able to see the W7 Partition and boot into it?  

Thanks

---

### Post by madverb on 2014-01-20
From Ubuntu have you tried [FONT=Courier New]update-grub[/FONT]

---

### Post by sports fan Matt on 2014-01-20
I had forgotten about that. Let me try that after the partition shrinks down :)

---

### Post by sports fan Matt on 2014-01-21
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by sports fan Matt on 2014-01-21
If a boot repair cannot fix this I shall be back.

---

### Post by sports fan Matt on 2014-01-21
it sees the Windows partition through GParted so I'm not sure what is wrong. Both W7 and the partition are seen, and if it helps I installed this through my thumb drive for now. (Yes I had to use WUBI) I'd like to be able to boot into Windows 7.

Any and all help is appreciated.

---

### Post by mastablasta on 2014-01-21
ah wubi s a totall different story. it is not in separate partition but rather in a virtual disk file. it uses windows boot manager to boot. so you didn't create partition but a virtual file. you might need to boot into live OS and then post results from botoinfo script here. to see where the boto loader is and how partitions disk is configured.

if windows partition is there then repairing the windows MBR might do the trick:  [https://support.microsoft.com/kb/927392](https://support.microsoft.com/kb/927392)

---

### Post by sports fan Matt on 2014-01-21
I found a Windows 7 disc that allowed me to boot and get Windows back. I will dual boot when my computer is returned.

---

