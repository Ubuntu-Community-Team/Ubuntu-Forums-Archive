---
title: "Add Fedora boot option in grub?"
date: 2007-04-29
forum: General Help
---

### Post by 67GTA on 2007-04-29
I use Ubuntu as my main OS, but like to play with others. I installed Fedora 7 and did not want it to take over grub since it may not stay installed. How can I make grub pickup on the partition? Is there a grub command that will accomplish this? I tried to mount the partition(sda4) but it said that it was not found in fstab. Update fstab? I was going to find the kernel in Fedora and add it to Ubuntu's grub list.

---

### Post by dcstar on 2007-04-30
> **67GTA said:**
> I use Ubuntu as my main OS, but like to play with others. I installed Fedora 7 and did not want it to take over grub since it may not stay installed. How can I make grub pickup on the partition? Is there a grub command that will accomplish this? I tried to mount the partition(sda4) but it said that it was not found in fstab. Update fstab? I was going to find the kernel in Fedora and add it to Ubuntu's grub list.

Lots of detailed posts in the forum on how to add Grub entries, just do a search for them.

---

### Post by Herman on 2007-04-30
Yes, or you could just add a configfile boot entry like this,

```
title                   Fedora Core 7 configfile boot on sda4
configfile          (hd0,3)/boot/grub/menu.lst
``` That should be all you need. Actually that is a better way to boot another Linux than a direct kernel boot. 

Regards, Herman :)

---

