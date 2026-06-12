---
title: "cannot install rpm with alien"
date: 2007-05-09
forum: General Help
---

### Post by Bashed on 2007-05-09
I installed Alien via Synaptic and then attempted to install the rpm via this method:

sudo alien -i soft-pro-3.0.0-154.rhel4.i386.rpm

I got these errors:

warning: soft-pro-3.0.0-154.rhel4.i386.rpm: Header V3 DSA signature: NOKEY, key ID 2425c37e
Warning: Skipping conversion of scripts in package soft-pro: postinst
Warning: Use the --scripts parameter to include the scripts.
warning: soft-pro-3.0.0-154.rhel4.i386.rpm: Header V3 DSA signature: NOKEY, key ID 2425c37e


So I tried to convert it to debian package:

sudo alien -d soft-pro-3.0.0-154.rhel4.i386.rpm


I then double clicked it and installed it via the debian manager, it went through without errors. However, when I click the shortcut icon it created in applications > system tools, absolutely nothing happens.

What should I do?

---

### Post by Lord Illidan on 2007-05-09
Any luck by starting it from the terminal?

Are there any sources provided?

---

### Post by Bashed on 2007-05-09
I do not even see any directory by its name in my /home/chad/ area (including hidden files).

The shortcut that was created shows this as command"

soft_pro

I ran that in command line and got this:

env: /usr/bin/swmc: No such file or directory


Attempted again to convert to deb package:

warning: soft-pro-3.0.0-154.rhel4.i386.rpm: Header V3 DSA signature: NOKEY, key ID 2425c37e
Warning: Skipping conversion of scripts in package soft-pro: postinst
Warning: Use the --scripts parameter to include the scripts.
warning: soft-pro-3.0.0-154.rhel4.i386.rpm: Header V3 DSA signature: NOKEY, key ID 2425c37e
soft-pro_3.0.0-155_i386.deb generated

---

### Post by fragos on 2007-05-09
Although an RPM can be converted to a DEB it still may not install correctly.  Even some DEB packages built for Debian won't install correctly on Ubuntu.

---

