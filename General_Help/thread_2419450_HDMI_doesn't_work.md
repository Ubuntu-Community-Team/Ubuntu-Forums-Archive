---
title: "HDMI doesn't work"
date: 2019-05-22
forum: General Help
---

### Post by pedrotainha on 2019-05-22
Hello, I have installed Ubuntu 18.04 in a lenovo thinkPad and my HDMI always worked well for display in a monitor. Yesterday i tried to instlall [https://www.displaylink.com/downloads/ubuntu](https://www.displaylink.com/downloads/ubuntu), for using a USB monitor from Asus. Installations seems running well but usb monitor dind't work ans worst than that, the HDMI seems not working anymore.

Can somebody help me troubleshooting to understand whats happening?

Thanks in advance

---

### Post by cruzer001 on 2019-05-22
I really don't have a good answer for this other than searching your file system and removing anything labeled "displaylink".  But then I would not know what to expect next.  Could fix it, could still be hose up even worst.

In the future if you want to experiment with packages consider installing a extra copy of Ubuntu for this or maybe a VirtualBox install or container and not hose your main system.

---

### Post by oldfred on 2019-05-22
Are you using 18.04 or 18.04.2 which I think has newer kernel?
You may need 4.18 kernel or newer. Or 19.04 which has even newer kernel.
You might try installing 19.04 in a 25GB / (root) partition just to test if that works.

[https://www.phoronix.com/scan.php?page=news_item&px=RH-DisplayLink-Driver-Improves](https://www.phoronix.com/scan.php?page=news_item&px=RH-DisplayLink-Driver-Improves)

---

