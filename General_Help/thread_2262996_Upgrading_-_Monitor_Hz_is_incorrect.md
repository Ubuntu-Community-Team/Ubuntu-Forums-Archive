---
title: "Upgrading - Monitor Hz is incorrect"
date: 2015-01-28
forum: General Help
---

### Post by lsutiger on 2015-01-28
I am upgrading from 10.04 to 14.04. In 10.04 I have NVIDIA Driver Version:195.36.24. In the Nvidia app the monitor shows as 1680X1050 @ 60 Hz. In 14.04 the display is a bit blurry and 1680X1050 does not have 60 Hz available. When trying to set to 60 with xandr (I believe that is the command - I am currently booting between the two installations), it states it is not available.

Any insight anyone can give me?

---

### Post by ibjsb4 on 2015-01-30
What driver are you running in 14o4?  If the 195 driver package carried over than maybe a driver upgrade would do some good.  I currently run the 331 driver and there is newer than that available.

---

### Post by lsutiger on 2015-01-31
Thanks for the reply. I upgraded to the nvidia 331.113  version. I have another problem though - it does not save. I have tried running as sudo, but it does not save and I have to run it every time. Could an edit in xorg do the trick?

EDIT: Just checked and the correct resolution and htz are in xorg.conf. But everytime I reboot Ihave to adjust it in the nvidia control panel.

---

### Post by ibjsb4 on 2015-02-02
Can the refresh rate be manually added to xrandr?

---

