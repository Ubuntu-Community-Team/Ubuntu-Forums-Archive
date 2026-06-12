---
title: "Automatic updates with unattended-upgrades. Is it a good idea?"
date: 2016-09-04
forum: General Help
---

### Post by david1981 on 2016-09-04
Hi All,

I have several Linux servers at my clients (Debian and Ubuntu without GUI) and I manually update them from time to time. I was thinking that it would be cool if the server would update itself automatically. I quickly found the package "unattended-upgrades" and I have a few questions:

- Do you think it is a good idea to let the server update itself? Is it a common method?
- My understanding is that this will only install security updates and patches and this will NOT upgrade to a later distro. I don't want to do any distro updates automatically.

My servers are mostly file servers, a few web servers. I could use this tutorial:
[https://wiki.debian.org/UnattendedUpgrades](https://wiki.debian.org/UnattendedUpgrades)

Thanks for your help!!

David

---

### Post by cariboo on 2016-09-04
I use [ucaresystem-core]("https://utappia.org/2016/03/28/ucaresystem-core-v3-0-released-and-available-in-ppa/"), to update servers, I run it manually, but it can be run as a cron job.

---

