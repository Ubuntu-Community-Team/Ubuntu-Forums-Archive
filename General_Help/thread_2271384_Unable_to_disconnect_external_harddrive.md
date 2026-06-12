---
title: "Unable to disconnect external harddrive"
date: 2015-03-29
forum: General Help
---

### Post by brent20 on 2015-03-29
Hi,

I currently have my seagate 2TB portable HDD connected to my laptop dualbooting Win8.1 / Ubuntu 14.04. I can't figure out how to safely remove the drive. I have tried to click the triangle eject button, right click te drive and click safely eject, right clicking safely eject from the launcher bar and I also tried to turn it off using the power button in the 'disks' menu. Every time I try this the drive turns off and immediately on again really fast, so there's no time to unplug it.

How can I turn the drive off and safely unplug it without it immediately reconnecting?


(Edit: grammar)

---

### Post by gordintoronto on 2015-03-30
If the drive has an icon on your desktop, and you right-click it and select "safely remove drive," and the icon disappears, you can disconnect it.

It's not clear what model of drive you have, but in my experience most external drives have a physical switch to power them down.

---

### Post by sandyd on 2015-03-30
Can you post the output of[code]sudo fdisk -l
mount -l[code]

Thanks

---

