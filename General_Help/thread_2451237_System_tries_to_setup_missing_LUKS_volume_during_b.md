---
title: "System tries to setup missing LUKS volume during boot"
date: 2020-09-29
forum: General Help
---

### Post by metacell on 2020-09-29
I had an encrypted Ubuntu installation on my main disk, and also an encrypted swap partition on my SSD.

I then removed and wiped my SSD, and commented out the lines for the swap partition in /etc/fstab and /etc/crypttab.

Now, when I reboot, Ubuntu only asks for one password, and says

```
Volume group "ubuntu-vg" not found
Cannot process volume group ubuntu-vg
Volume group "luks" not found
Cannot process volume group luks
```

After a few minutes it drops me to the (initramfs) prompt.

Running boot-repair from the Ubuntu installation disk doesn't make any difference.

How do I make my system bootable again?

---

