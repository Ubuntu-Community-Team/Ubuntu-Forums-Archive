---
title: "Problems with dual boot and bluetooth"
date: 2017-03-13
forum: General Help
---

### Post by dinisov on 2017-03-13
Hello,

I am running 16.04 together with windows 10. The symptoms are the following:

After booting into windows, if I shut down and boot into ubuntu, it fails with the following message:

Bluetooth: hci0: Setting Intel event mask failed (-16)

The only way to solve this problem seems to be to boot into windows, restart (not shut down) and then choose ubuntu in grub.

If I don't boot into windows, there are no problems booting into ubuntu.

Thanks in advance for any help!

Dinis

---

### Post by wyliecoyoteuk on 2017-03-13
This is because Windows is leaving the firmware on the Bluetooth adapter in an altered state, which unfortunately stops Ubuntu accessing it.
You might be able to reload it.
What make/model of Bluetooth adapter?

---

### Post by dinisov on 2017-03-13
Thanks for your help!

lspci yields

04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)

and looking at my thinkpad T460's specs online it seems that matches this

11ac+BT, Intel Dual Band Wireless-AC 8260, 2x2, M.2 card

---

### Post by wyliecoyoteuk on 2017-03-13
Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1590985](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1590985)

---

### Post by dinisov on 2017-03-15
The post you recommend is not about dual booting nor BT. If you are suggesting updating the BIOS (UEFI really) I had thought of that, but I need to back everything up and I would like to avoid it because extensive experience tells me that BIOS updates solve nothing. Not to mention the laptop is a few months old and unlikely to suffer from an old BIOS. You mentioned that I might be able to reload it?

---

### Post by wyliecoyoteuk on 2017-03-15
Hi, sorry, that was a follow on from another post where they were experiencing the same issue with the Intel 8260, which is a dual band wifi and bt card. 
I got wifi and bluetooth mixed up.
It still boils down to a firmware (not BIOS) issue.
Most wifi or BT adaptors need their firmware loaded at boot time, if it is failing after a cold boot, it probably needs the correct firmware loading from Linux.
This might help.
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1476900](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1476900)

---

### Post by dinisov on 2017-03-20
Thanks again for the help. Sorry for the delay. The new link also does not help. It seems to be an issue with older versions of ubuntu, and I am running 16.04.

---

