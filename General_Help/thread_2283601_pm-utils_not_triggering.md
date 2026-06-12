---
title: "pm-utils not triggering"
date: 2015-06-23
forum: General Help
---

### Post by oscar-tiderman on 2015-06-23
Hi, since upgrading to 15.04 my power saving scripts seems to never kick in. As far as I can telll "pm-powersave true" is never triggered, like when I boot on battery or when unplugging my charger. I have checked /var/log/pm-powersave.log doesn't log any events. If I manually run "pm-powersave true" the powersaving mode is triggered as expected. If I run acpi_listen I can see that the charger unplug event is registered correctly. What could have caused the automatic triggering of "pm-powersave true" to stop working? It was working just fine before upgrading to 15.04. Any advice or thought about this would be appreciated. How can I troubleshoot it further? I'm kind of stuck here.

---

### Post by oscar-tiderman on 2015-07-02
This is a bug caused by the switch to systemd, details here: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1461386](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1461386)

---

