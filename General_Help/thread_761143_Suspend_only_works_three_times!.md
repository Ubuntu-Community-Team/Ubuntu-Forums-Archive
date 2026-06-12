---
title: "Suspend only works three times!"
date: 2008-04-20
forum: General Help
---

### Post by tylerious on 2008-04-20
I seem to have a similar problem to [http://ubuntuforums.org/showthread.php?t=658932](http://ubuntuforums.org/showthread.php?t=658932)
My problem, however, is different since I do not have a JMicron ATA controller.

I can suspend and resume three times successfully. When I hit a key to resume the fourth time, the fans spin as if it's waking up (and I think the HD spins too), but the power light continues to flash as if it's asleep and the screen never wakes up.

I've tried adding acpi_sleep=s3_mode to my kernel params and tried changing a few things in /etc/default/acpi-support, but nothing has helped.

I seem to recall having a similar problem (but waking up less) a while ago when I first tried Gutsy. A lot has been updated since then, so I don't know why conditions have changed.

I am running Gutsy Ubuntu with the binary NVIDIA driver (100.14.19+2.6.22.4) and generic kernel 2.6.22-14.

---

