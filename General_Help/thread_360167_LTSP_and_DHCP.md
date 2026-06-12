---
title: "LTSP and DHCP"
date: 2007-02-12
forum: General Help
---

### Post by szquirrel on 2007-02-12
This is an answer rather than a question, because I'm sure I can't be the only person to struggle with this.

I'm not a Linux expert. For the last few weeks I've been setting up some test Ubuntu servers and for the most part it has been painless.

Until today. I wanted to set up a LTSP server but for various reasons I wanted to use Ubuntu rather than Edubuntu. That's fine, I found some step-by-step LTSP instructions and followed them, and everything looked good until my DHCP suddenly refused to start. I read all of the man pages I could find, tried a dozen different configs, uninstalled, reinstalled, and basically did everything I could think of to fix it.

It turns out that the /etc/init.d/dhcp3-server script actually looks for a /etc/ltsp/dhcpd.conf file, and if it finds that one it ignores the standard /etc/dhcp3/dhcpd.conf file. I don't know if it was always that way or if installing LTSP somehow modified the dhcp3-server script, but there it is. I've been editing the wrong conf file and it took me way too long to figure that out.

You know where would be a good place to include this info? **ANYWHERE.** :mad:

---

