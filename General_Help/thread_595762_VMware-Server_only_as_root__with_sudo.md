---
title: "VMware-Server only as root / with sudo"
date: 2007-10-29
forum: General Help
---

### Post by Manu on 2007-10-29
Hi all,

I installed VMware from the tar-archive and did nothung special. However, I can only start vmware with sudo.
This is obvious when looking at the file permissions of the created files. /usr/bin/vmware is only readable and executable by root. :( When I change some of the permissions manually vmware will start as user but can't boot machines afterwards. Doesn't seem to be a neat way, though.

What did I do wrong? (I apparently did nothing wrong.) Is it because of UMASK 077 on my system?

Any help is appreciated. :)

---

### Post by Manu on 2007-10-29
umask 0022 did the trick. Don't ask why. ;)

---

