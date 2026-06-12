---
title: "port knocking anyone?"
date: 2005-06-30
forum: General Help
---

### Post by jfdill_2 on 2005-06-30
Anyone using port knocking on Ubuntu and if so what implementation?  I imagine there is probably something in the Universe, but it may take a little bit to dig it up.

For the uninitiated, [port knocking](http://www.portknocking.org/view/) is a technique for keeping a port (for example SSH) closed all the time, but allowing it to open when a special sequence of packets is sent to the host.  The technique is touted as a way to deal with brute force attacks on SSH, which is exactly why I started looking into it.

---

### Post by jfdill_2 on 2005-07-01
I found that [knock](http://www.zeroflux.org/cgi-bin/cvstrac/knock/wiki) is in the Universe repository, and seems pretty simple to configure and use.  But...I haven't got it to play nicely with firehol as yet.

I think approaches like [Doorman](http://doorman.sourceforge.net/)  and [tumbler](http://tumbler.sourceforge.net/) might be easier to configure in terms of an external firewall with firewall rules since they use a single port.  But then, Why not just use key-based authentication and turn off password auth to ssh?  Or just use some sort of VPN and don't allow ssh from the outside without it.

I think the whole value of port knocking would mainly be for "emergency" access from some place where I don't usually connect and do not want to install a VPN client.  In which case, it's got to be easy to do with basic tools that are available, like putty and a web browser.  Also opening up to an IP address seems like a bad idea--if you are coming from a NATed network, you just opened that port to the whole entire network that you connected from.

---

