---
title: "Domain Problem"
date: 2007-11-01
forum: General Help
---

### Post by tj71587 on 2007-11-01
I named my computer webserver in the /etc/hosts file and the only place typing webserver in the web browser works is on that specific computer.  I just want to alias it for the intranet.  What else do I have to do?

```

127.0.0.1		localhost.localdomain localhost
192.168.1.5		webserver.networkserver.com webserver
::1		localhost6.localdomain6 localhost6

```

All I want is for people on my network to type webserver in the browser and for it to go to 192.168.1.5  What else must I do.  Thanks.

---

### Post by dcstar on 2007-11-02
> **tj71587 said:**
> I named my computer webserver in the /etc/hosts file and the only place typing webserver in the web browser works is on that specific computer.  I just want to alias it for the intranet.  What else do I have to do?

```

127.0.0.1		localhost.localdomain localhost
192.168.1.5		webserver.networkserver.com webserver
::1		localhost6.localdomain6 localhost6

```

All I want is for people on my network to type webserver in the browser and for it to go to 192.168.1.5  What else must I do.  Thanks.

You have to either set up your own DNS server with this entry, or manually edit all the other PCs' hosts files with an identical entry.

---

### Post by tj71587 on 2007-11-02
Is there a good howto on how to setup a dns server anywhere?  Thanks.

---

### Post by dcstar on 2007-11-02
> **tj71587 said:**
> Is there a good howto on how to setup a dns server anywhere?  Thanks.

There should be quite a few around, you will have to search them out.

If you do set up your own DNS, then all the other PCs have to know to use it - so you will have to either make that change in their own DNS entries or the DHCP server that sets up their DNS.

The whole setup is not trivial.

---

### Post by surfer69 on 2007-11-02
I have a similar problem, I've just introduced my frst Ubuntu server to my win2003 domain, but I can't resolve the machine name to an ip address.

Eventually I will be changing over to an entirely Ubuntu network.

This is all set up at home, with 6 kids and me and my partner online at the same time sometimes.

---

### Post by tj71587 on 2007-11-03
I am still stuggling to find a tutorial to make a domian server.  I could use either my ubuntu one or my centos one, if anyone knows of a good tutorial please post here.

---

### Post by dcstar on 2007-11-03
> **tj71587 said:**
> I am still stuggling to find a tutorial to make a domian server.  I could use either my ubuntu one or my centos one, if anyone knows of a good tutorial please post here.

Here's what took me 10 seconds of searching to find:

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

