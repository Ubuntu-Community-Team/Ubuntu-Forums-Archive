---
title: "Syology like web server interface?"
date: 2023-06-11
forum: General Help
---

### Post by josephchrzempiec on 2023-06-11
Hello, I was curious if anyone has made a Web interface like Synology? I have been searching around. I also tried to start one myself and well lets say it ended up badly. 

Joseph

---

### Post by TheFu on 2023-06-12
> **josephchrzempiec said:**
> Hello, I was curious if anyone has made a Web interface like Synology? I have been searching around. I also tried to start one myself and well lets say it ended up badly. 

Joseph

You mean like FreeNAS/TrueNAS? [https://nascompares.com/2022/03/21/truenas-core-software-review-gui-design-storage-management/](https://nascompares.com/2022/03/21/truenas-core-software-review-gui-design-storage-management/)

Or a general admin interface like webmin [https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-webmin-on-ubuntu-22-04)
or Cockpit [https://www.howtogeek.com/702841/how-to-manage-linux-servers-with-the-cockpit-web-interface/](https://www.howtogeek.com/702841/how-to-manage-linux-servers-with-the-cockpit-web-interface/)

I'm anti-server admin via GUIs, because they make attacks too easy for people who don't set them up to only allow localhost connections. Last thing we need is a webapp which can be trivially hacked, but has the full power of an admin to destroy/reconfigure a system.

QNAP and Synology have been hit more than 2x every year with security problems mainly due to their webapps.

Please reconsider these webapp tools, if you aren't 100% certain of your LAN security. I've been at this 30 yrs now and I'm not certain about my LAN security.  It you do go forward, please, please, please, setup firewall rules on the machine that block all systems, even your own, that have no business managing the server.

As with all security, provide the least authority possible for each client to accomplish the specific tasks it needs to do.  If it needs read-only access to storage, only provide read-only access to the specific storage required. No more.

---

