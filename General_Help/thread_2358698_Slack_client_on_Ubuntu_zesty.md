---
title: "Slack client on Ubuntu zesty"
date: 2017-04-16
forum: General Help
---

### Post by xeperis2 on 2017-04-16
So I grabbed the latest Ubuntu of the shelf.

Everything is working ok, except I can not install Slack: [https://slack.com/downloads/linux](https://slack.com/downloads/linux)
I downloaded the .deb package and when I open it with `Ubuntu Software` the install button does nothing (same for other packages).
I tried using GDebi (like I did for the rest of software) but it fails half way through: "(Reading database ... 55%".

Has anyone encountered something similar?

---

### Post by howefield on 2017-04-16
Try it with apt.. seems to work here on a fresh zesty install

```
sudo apt install -  ~/Downloads/slack-desktop-2.5.2-amd64.deb 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'slack-desktop' instead of '/home/hugh/Downloads/slack-desktop-2.5.2-amd64.deb'
The following additional packages will be installed:
  gconf2
Suggested packages:
  gconf-defaults-service
The following NEW packages will be installed
  gconf2 slack-desktop
0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Inst gconf2 (3.2.6-3ubuntu7 Ubuntu:17.04/zesty [amd64])
Inst slack-desktop (2.5.2 local-deb [amd64])
Conf gconf2 (3.2.6-3ubuntu7 Ubuntu:17.04/zesty [amd64])
Conf slack-desktop (2.5.2 local-deb [amd64])
```

---

### Post by xeperis2 on 2017-04-16
Thanks, this printed out what was going on. Apparently [https://launchpad.net/ubuntu/+source/slack](https://launchpad.net/ubuntu/+source/slack) package collided with slack client package.

---

### Post by howefield on 2017-04-16
> **xeperis2 said:**
> Thanks, this printed out what was going on. Apparently [https://launchpad.net/ubuntu/+source/slack](https://launchpad.net/ubuntu/+source/slack) package collided with slack client package.

Cool, you're welcome.

---

