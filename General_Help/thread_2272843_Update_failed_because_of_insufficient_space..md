---
title: "Update failed because of insufficient space."
date: 2015-04-08
forum: General Help
---

### Post by MagisterDixit on 2015-04-08
OK, so I'm on Ubuntu 14.04 LTS. Ubuntu is my only operating system on this computer and I have next to nothing stored on it. Yet, I get an error when I try to do an update that claims I'm out of room. The disk analyzer shows that the majority of my computer is unused. I left the defaults alone during installation. What is going on and how do I fix it? I supplied a pic of the error and the disk analyzer just in case I am explaining poorly.
[ATTACH=CONFIG]261184[/ATTACH]

---

### Post by grahammechanical on 2015-04-08
Did you notice the bit about needing free space on "disk /boot?" You have a boot partition and that is what is almost full. The update most likely wants to install an updated kernel and there is no space to do that.

Try point Disk analyser to the boot partition. Or loading Recovery mode from the Advanced Options menu and then selecting Clean - try to create free space.

Regards.

---

