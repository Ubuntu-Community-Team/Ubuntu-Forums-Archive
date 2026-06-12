---
title: "Upgraded from 13.10 to 14.04 - dual boot windows 7 - Unable to boot - Boot repair"
date: 2014-04-28
forum: General Help
---

### Post by posushant on 2014-04-28
[h=2][/h][COLOR=#000000][INDENT]System Dual Boot - Windows 7 and Ubuntu 
I upgraded from 13 to 14.04 and have dual boot windows 7 that was working fine. Since upgrading the version 14.04 is not booting shows three options Press I to ignore S to skip mounting and M manual recovery
Tried two solutions
1. Boot-repair - Although showed it is successful the system was in the same state not booting 
Here is what i got [http://paste.ubuntu.com/7347032/](http://paste.ubuntu.com/7347032/)

2. Also tried changing ro to rw in grub file- by choosing manually repair. Performed following
[COLOR=#000000]vim /boot/grub/grub.cfg
[FONT=Verdana]
Looked for line similar to this (search for the [/FONT]**highlighted part):**[/COLOR]
[B]Code:
linux /boot/vmlinuz-3.13.0-24-generic root=UUID=[bunch-of-numbers] loop=/ubuntu/disks/root.disk **ro rootflags=sync** quiet splash
[/B][B]Tried Changing the ro to rw (as in - instead of mounting as read-only, mount for read-write)
[/B]
But the vim does not allow me to write .. i changed permissions etc. it did not help 

also looked for .viminfo! duplicate - it is not there 
----------------------------------------------[/INDENT]
[/COLOR]

---

### Post by oldfred on 2014-04-28
You have a wubi install, not many of us here use wubi and know much about it.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04](http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04)

Wubi also is being discontinued as it does not work with gpt partitioned drives which all new UEFI systems have.
Last supported version of wubi is 12.04, beyond that it can supposed be used but requires advanced knowledge to maintain yourself. And that is the opposite of what wubi is supposed to be. 

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.



If you like Ubuntu it may be time to repartition and do a full install.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by hakuna_matata on 2014-04-28
> **posushant said:**
> [COLOR=#000000][INDENT]2. Also tried changing ro to rw in grub file- by choosing manually repair. Performed following
[COLOR=#000000]vim /boot/grub/grub.cfg[/COLOR]
[/INDENT]
[/COLOR]
IMHO problem is that whole partition is only mounted with read access.

Try this: [http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)

---

