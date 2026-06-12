---
title: "isolcpus not working after suspend?"
date: 2014-09-10
forum: General Help
---

### Post by go3d on 2014-09-10
How can I determine if the boot parameter **isolcpus** (in /etc/default/grub + command "update-grub") is effective at any given moment? My problem is that, after setting this parameter for my project as needed, things work as they should after reboot. But when I suspend and resume the PC, apparently the cpus are not isolated anymore.

So my questions are:

1. Is the isolcpus setting lost after suspend/resume? And if yes, how can I re-enable it without reboot?

2. How can I determine for sure if the isolcups setting is actually active?

---

