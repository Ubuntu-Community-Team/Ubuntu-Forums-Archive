---
title: "can't connect to server via ssh."
date: 2005-10-25
forum: General Help
---

### Post by bb002 on 2005-10-25
I've got a Ubuntu 5.04 sever all and I was going to install ssh to remote admin.

I opened a terminal and did "sudo apt-get install ssh" everything went fine. However I can't to the server from another machine with "ssh bb002@192.168.224.23" I get connection refused immediately. I also tried without the bb002 still won't work.

I've checked that the ssh daemon is running but i still get connection refused.

---

### Post by bb002 on 2005-10-25
Got it. Seems something goofed during the install...When i tried to remove the package it told me it wasn't installed. Yet, I could /etc/init.d/ssh start|stop|restart. Strange. I did "sudo apt-get install ssh" and everything worked this time.

---

