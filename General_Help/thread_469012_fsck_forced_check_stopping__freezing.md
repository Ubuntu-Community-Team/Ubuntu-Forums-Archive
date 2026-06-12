---
title: "fsck forced check stopping / freezing"
date: 2007-06-09
forum: General Help
---

### Post by webcrawler42 on 2007-06-09
Whenever I start my computer fsck says that the drive has been mounted 24 times without a check and the check is being forced, then it stops/freezes and doesn't go any farther and I can't do anything, if I press enter it does nothing.

---

### Post by webcrawler42 on 2007-06-10
Found an answer on another forum

[http://forums.devnetwork.net/viewtopic.php?p=377659&sid=c496cd4a57178f3c9f3a40e2e8d8ca6f](http://forums.devnetwork.net/viewtopic.php?p=377659&sid=c496cd4a57178f3c9f3a40e2e8d8ca6f)

"I can confirm changing last digit on the end of the root filesystem in /etc/fstab to '0' disables forced FSCK check of drives."

---

