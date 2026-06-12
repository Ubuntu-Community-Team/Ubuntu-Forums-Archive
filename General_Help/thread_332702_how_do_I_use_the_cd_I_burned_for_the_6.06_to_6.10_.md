---
title: "how do I use the cd I burned for the 6.06 to 6.10 upgrade?"
date: 2007-01-06
forum: General Help
---

### Post by Scott A on 2007-01-06
how do I use the cd I burned for the 6.04 to 6.10 upgrade?

---

### Post by aysiu on 2007-01-06
You mean 6.06 to 6.10?

If it's the Alternate CD, you use these terminal commands: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.dapper.list
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
``` If it's the Desktop CD, you need to reinstall or upgrade over the internet.

---

