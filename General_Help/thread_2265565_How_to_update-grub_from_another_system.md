---
title: "How to update-grub from another system?"
date: 2015-02-16
forum: General Help
---

### Post by marcin23 on 2015-02-16
Hi all,

I have a little problem - I've installed Ubuntu Server 14.04 on SDA, Fedora 20 on SDB. When I am logged to Fedora I must mount SDA and edit grub.cfg file in /etc/default/grub.cfg and restart machine, boot Ubuntu with changes. As we now, after editing this file we must run update-grub command - and it's problem - on Fedora I can't run update-grub, because Fedora have antoher command for Fedoras GRUB.

Anyone know how can I update mounted Ubuntu GRUB from Fedora system?

---

### Post by philinux on 2015-02-16
I use chroot. 
whatever is your chosen directory. You'll need to create the /mnt/whatever directory first. Once in a chroot you can update the system, run update-grub. Anything. I run this as a script.
```
#!/bin/sh

##sudo mkdir /mnt/whatever
sudo mount /dev/sdb1 /mnt/whatever/
sudo mount -o bind /proc /mnt/whatever/proc
sudo mount -o bind /dev /mnt/whatever/dev
sudo mount -o bind /dev/pts /mnt/whatever/dev/pts
sudo mount -o bind /sys /mnt/whatever/sys
sudo cp /etc/resolv.conf /mnt/whatever/etc/resolve.conf
sudo chroot /mnt/whatever /bin/bash

fi
```

---

### Post by marcin23 on 2015-02-16
Ok thanks, but I forgot about grub.cfg - "update-grub" command write to /boot/grub/grub.cfg - if I edit this file (set_default), GRUB default option will change without update-grub.

---

### Post by grahammechanical on 2015-02-16
In Ubuntu update-grub is a script and so is update-grub2 and they both do the same thing. They run grub-mkconfig.

/usr/sbin/update-grub

> #!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"


I do not use Fedora so I do not know if they have a Fedora equivalent. I do not know where Fedora keeps its Grub files. But grub-mkconfig is the Grub Command according to the Grub manual.

Regards.

---

