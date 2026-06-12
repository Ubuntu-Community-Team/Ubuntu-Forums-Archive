---
title: "Live cd 13.10 disable mounting of all internal drives"
date: 2014-04-07
forum: General Help
---

### Post by leeinwv on 2014-04-07
I have created a live cd using UCK and 13.10. This will be used on different computers and I want to remove the ability to mount any internal drives the iso is being used on.
I would prefer not to even be able to read the internal drives if possible. Has anyone had any luck doing this?

Any assistance is greatly apreciated.

---

### Post by leeinwv on 2014-04-09
Some progress. Using the method described from this link [http://askubuntu.com/questions/156894/disable-mount-for-internal-hdds](http://askubuntu.com/questions/156894/disable-mount-for-internal-hdds), I have been able to stop the automount of the internal hard drives.
I edited and copied /etc/udev/rules.d/60-persistent-storage.rules into /etc/udev/rules.d and added sda* and sdb*, then reconstructed the live cd. I can still manually mount from a terminal using mount -t ntfs /dev/sda1 /mnt, but the internal drives do not automatically appear at boot.

---

