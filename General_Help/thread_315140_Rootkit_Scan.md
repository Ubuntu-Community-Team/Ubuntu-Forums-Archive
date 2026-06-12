---
title: "Rootkit Scan"
date: 2006-12-08
forum: General Help
---

### Post by SmiLey497 on 2006-12-08
i got this running a rootkit scan with rkhunter. is thi ssomehtign to worry about or just fals epositives

Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory)

---

### Post by streeto on 2007-01-12
Had this problem too, Just uncomment these lines in /etc/rkhunter.conf.

ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENDIR=/dev/.udevdb
ALLOWHIDDENDIR=/etc/.java

---

### Post by lotusleaf on 2007-01-12
> **streeto said:**
> Had this problem too, Just uncomment these lines in /etc/rkhunter.conf.

ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENDIR=/dev/.udevdb
ALLOWHIDDENDIR=/etc/.java

An awesome tip, thanks :)

---

