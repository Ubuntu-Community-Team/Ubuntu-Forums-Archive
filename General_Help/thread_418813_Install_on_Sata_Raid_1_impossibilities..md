---
title: "Install on Sata Raid 1 impossibilities."
date: 2007-04-22
forum: General Help
---

### Post by SOG420 on 2007-04-22
I have a Dell XPS5 with two sata 150 GB set up in a raid 1 configurations. I have tried to install multiple windows OS as well as Ubuntu Dapper and Edgy. The install stops at the partion screen in windows and almost immediaty in Ubuntu. I called dell support and as usual the were no help and told me to install the original windows OS and install Raid drivers on a floppy durring installation. This is impossible seeing as I don't have a floppy drive. Any help would be appreciate it cuz as of right now I have a $1700 paperweight

---

### Post by dcstar on 2007-04-22
> **SOG420 said:**
> I have a Dell XPS5 with two sata 150 GB set up in a raid 1 configurations. I have tried to install multiple windows OS as well as Ubuntu Dapper and Edgy. The install stops at the partion screen in windows and almost immediaty in Ubuntu. I called dell support and as usual the were no help and told me to install the original windows OS and install Raid drivers on a floppy durring installation. This is impossible seeing as I don't have a floppy drive. Any help would be appreciate it cuz as of right now I have a $1700 paperweight

Go into the BIOS and disable the RAID and then try an install (or physically unplug one SATA drive)

You can always turn the RAID back on post-install and all it should (hopefully) do is mirror the good drive to the uninstalled one.

---

