---
title: "Windows Vista disappeared?"
date: 2008-01-27
forum: General Help
---

### Post by jbernhardt on 2008-01-27
Hey, I just reinstalled ubuntu after switching from another distribution because ubuntu wasn't supporting my sound card. It appears that GRUB has taken over though and I can't boot into windows anymore.

Partition 1 is windows vista main partition (ntfs)
Partition 2 is a 100 mb extended partition
Partition 5 is ubuntu
partition 6 is a memory swap
partition 4 is windows vista recovery partition (ntfs)

Does this look weird to anyone? If you could tell me how to modify grub to boot back into windows, I'd really appreciate it.

---

### Post by matthewcraig on 2008-01-27
Sorry to hear you are having an issue.  GRUB is required for a dual-boot configuration.  Is there an entry in the configuration file so your version of a Windows operating system is listed and selectable in the menu?

---

### Post by Ub1476 on 2008-01-27
To see your partitions:

```
sudo fdisk -l
```

Graphical Grub editor: [QGRUBEditor]("http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391")

---

### Post by Raccoon1400 on 2008-01-27
I had to do this a few minutes ago.
This is part of a tutorial I wrote.
It shows a few other modifications too. The one you need is in green.

Root login is disabled by default, so here's how to change it.
go to system>administration>login window. under the security tab, enable local system admin login.

Go to welcome screen, log in as root(root is username, and then enter admin password)

navigate to /boot/grub/menu.1st

The file should look like this.
my notes are in colour.
#lines are commented out.(have no effect)d)
## ## End Default Options ##

title Ubuntu 7.10 ubuntu(entry 0)
root (hd0,4)the partition this command boots.
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e63a103e-8c6f-4f34-9ebf-0b3f7f607967 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3 [COLOR="Lime"]here is my vista entry. add an entry like this to the file[/COLOR].
title Windows Vista vista(entry 1)
root (hd0,2)[COLOR="Lime"] this is the partition the command will boot.[/COLOR]
savedefault
makeactive
chainloader +1

title Ubuntu 7.10 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e63a103e-8c6f-4f34-9ebf-0b3f7f607967 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title Other operating systems: this divider usually has windows after it, but I moved it and commented this part out for neatness.
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Dell Utility
root (hd0,0)
savedefault
makeactive
chainloader +1

---

