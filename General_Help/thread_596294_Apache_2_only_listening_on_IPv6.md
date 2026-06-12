---
title: "Apache 2 only listening on IPv6"
date: 2007-10-29
forum: General Help
---

### Post by zeroomegazx on 2007-10-29
How can I change which address httpd listens on.  Its currently set to listen on 6 instead
of 4.  I've searched google and quite a few forums.  I'm sure there is some simple way to do it.  I have a base install of Ubuntu 7.10 and apache2 (latest release)  and cannot get anyone to connect to me or web browsing on the internal network.  I can get the pages to come up on the machine itself through local loop back. Any help would be most appriciated!

---

### Post by p_quarles on 2007-10-29
I'm curious how you know it's listening on an ipv6 address. The default installation listens on port 80, without specifiying any ip address. 

Anyway, I don't use the Ubuntu setup of Apache, so I'm not sure I remember exactly where the file is, but I think it's something like /etc/apache2/ports.conf. The "ports.conf" part I know is correct, but I don't know exactly which directory. Can you post the contents of that file?

---

### Post by zeroomegazx on 2007-10-30
The ports are fine, it is setup to listen on 80, i haven't changed any setup at all, When I do a netstat -l -t i see the service listening on TCP6.  If i disable IPv6 in aliases it works fine, but that really isn't the solution i am looking for.  Apache can listen on IPv6 and IPv4 for specific virtual hosts, but I haven't added or changed any of the default settings and from what I can see there is no setup for listening on only IPv6 in the current host config.  It seems to be listening on all IP's

---

