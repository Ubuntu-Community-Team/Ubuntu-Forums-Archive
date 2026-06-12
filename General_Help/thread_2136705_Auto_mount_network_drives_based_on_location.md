---
title: "Auto mount network drives based on location"
date: 2013-04-18
forum: General Help
---

### Post by iceman55 on 2013-04-18
Is there a way to automount drives depending on your location, or more specifically depending on which network you are connected to?

I have a Lenovo laptop for work running Ubuntu 13.04 which I take home and travel with. At the moment I am mounting remote machines using SSHFS and NFS via command line when I'm in the office. What I would like to do is automate the process so that when I am at work my machine will automatically mount those drives. Is this possible? I suppose I could simply set them to mount on boot but I'm not sure how that will behave when I am not in the office.

---

### Post by Toz on 2013-04-18
You might want to consider using [autofs]("https://help.ubuntu.com/community/Autofs"). It will automatically mount your shares when you try to access them and unmount them after a period of inactivity.

---

