---
title: "Help mounting to a Specific Location"
date: 2007-07-05
forum: General Help
---

### Post by Darko Beta on 2007-07-05
I have a couple of different MP3 players and a USB hard drive.  Is there a way to get each of them to mount to a specific physical location each time they are connected?  For example, /dev/sdb or /dev/sdc?  I customized their icons, and if they don't connect to the right locations then they have the wrong icons.  Or, similarly, is there a way to attach the icon selection to the mount point rather than the physical location?

I examined an article about understanding fstab, which seemed related to this, but couldn't find an answer to this particular question.

---

### Post by kuja on 2007-07-05
Perhaps by placing a .directory file or similar in the drives root directory it will use that icon when mounted? Perhaps anyway. Anyhow. HAL mounts it to the first available device AFAIK, and I don't think that can be changed.

---

