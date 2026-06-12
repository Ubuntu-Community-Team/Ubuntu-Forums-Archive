---
title: "Delete Windows XP from Partitioned drive"
date: 2013-01-30
forum: General Help
---

### Post by worldtraveller321 on 2013-01-30
Hello all I just installed Ubuntu on my computer, a Netbook, original operating system is Windows XP
in which i partitioned my drive to have both on it
i want to free up my drive space and delete all of Windows XP

what way can i safely delete all of Windows XP
without loosing my Ubuntu installation?

thanks

---

### Post by TheFu on 2013-01-30
First, if you use WUBI, don't do this.
Use** gparted** to delete the Windows partition(s).
If it doesn't boot afterwards, use **boot-repair **to correct that.

If you want to move your Linux partition(s) around, boot off a DVD/CD or flash drive with **gparted** ISO and move the partitions around, then resize them as desired. It is not possible to modify partitions with a currently running OS, hence the need to boot off some other media for this part.

---

