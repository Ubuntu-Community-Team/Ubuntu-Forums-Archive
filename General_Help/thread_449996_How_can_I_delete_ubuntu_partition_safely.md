---
title: "How can I delete ubuntu partition safely?"
date: 2007-05-20
forum: General Help
---

### Post by djvic87 on 2007-05-20
I need to delete the ubuntu partition off my laptop because I need the memory back. Can someone please tell me how I can delete the partition? I dont have the xp boot cd but I have the ubuntu live cd.

Also, can someone tell me the other partitions that I need to delete as well? thanks.

---

### Post by bobplano on 2007-05-20
you can boot from the live cd and go to system>administration>gnome partition manager. then delete your partitions. you can also delete these using window's partition manager.

---

### Post by confused57 on 2007-05-20
> **djvic87 said:**
> I need to delete the ubuntu partition off my laptop because I need the memory back. Can someone please tell me how I can delete the partition? I dont have the xp boot cd but I have the ubuntu live cd.

Also, can someone tell me the other partitions that I need to delete as well? thanks.

Don't just delete your Ubuntu partitions or you won't be able to boot Windows...see this guide:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
since you don't have a Window's install cd, you can use a Win98SE oem boot floppy, or the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You basically need to restore your Window's IPL code to the mbr, before deleting your Ubuntu partitions.

---

