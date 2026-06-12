---
title: "No Suspend option in Cinnamon after migration to Ubuntu Vivid 15.04"
date: 2015-04-21
forum: General Help
---

### Post by adlerhn on 2015-04-21
I am a Ubuntu GNOME user, and I usually use the Cinnamon DE.

Suspend was working perfectly until right before the migration to Ubuntu Vivid 15.04. I had the Suspend menu option, and the computer would suspend as well when the lid close.

Right after migration to 15.04, my computer has lost the capability of suspending within Cinnamon (the Suspend option has disappeared altogether). If I use Unity or GNOME, the Suspend option is there, and the laptop suspends just fine. So, this issue affects only Cinnamon with Ubuntu 15.04.

The Cinnamon team states that some Systemd and Upstart libraries may be missing in Ubuntu: [https://github.com/linuxmint/Cinnamon/issues/4060](https://github.com/linuxmint/Cinnamon/issues/4060)

I have opened a bug report to Systemd ([https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1446276](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1446276)), but I am not sure whether this is an actual issue in Systemd and Upstart, or just something that has changed and Cinnamon does not support it.

How could I know for sure whether this is a misconfiguration in my side, a bug in Ubuntu (Systemd?), or in Cinnamon?

---

