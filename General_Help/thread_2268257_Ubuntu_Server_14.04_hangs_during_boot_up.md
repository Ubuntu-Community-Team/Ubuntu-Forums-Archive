---
title: "Ubuntu Server 14.04 hangs during boot up"
date: 2015-03-07
forum: General Help
---

### Post by redmattski on 2015-03-07
Hi

I have Ubuntu Server 14.04 installed as a virtual machine on my home server.  It had been work fine and I had set up a LAMP server (substituting in MariaDB) on which to run Owncloud, Piwigo and Wordpress.

However, after a power outage, when restarting the VM, the OS hangs during start up, MariaDB (MySQL) has been initialised.

I can connect into the computer via SSH and I have tried to dentfy the root cause of this issue.  However, I have not been able to identify the root cause of the problem.

Can anyone suggest how to identify the issue?  I can just create a new VM but I would really like to understand the root cause and bnuld a better understanding of the start up process.

My dmesg output is located here:  [http://pastebin.com/AN6gxrtM](http://pastebin.com/AN6gxrtM)

My syslog output is located here:  [http://pastebin.com/LGjGCtXF](http://pastebin.com/LGjGCtXF)

My boot.log output is located here:  [http://pastebin.com/JTUtbG01](http://pastebin.com/JTUtbG01)

---

