---
title: "Bind9 does not work.  Network Manager set to manuel address.  Can't make my own DNS"
date: 2017-03-21
forum: General Help
---

### Post by MechaMechanism on 2017-03-21
I installed Bind9 and set the settings in Network Manager to manual and input my static LAN address.  I put 127.0.0.1 as my DNS server.  When I restart the computer so the settings take effect, I test Firefox and it can not find web pages.  When setting the DNS to 192.168.0.1 for the router which itself uses 8.8.8.8 and 8.8.4.4 the DNS works and Firefox finds web pages.  I installed Bind9 and made no alterations to the files in /etc or anywhere else.

I use;
Ubuntu 16.10
Desktop

All updates applied as of today.

I would like my own recursive DNS to test and experiment on.  Any help is much appreciated.

```
Mar 21 22:10:19 frontier systemd-resolved[1487]: Using degraded feature set (TCP) for DNS server 127.0.1.1.
Mar 21 22:10:27 frontier systemd-resolved[1487]: Using degraded feature set (UDP) for DNS server 127.0.1.1.
Mar 21 22:10:27 frontier kernel: [   79.504499] TCP: request_sock_TCP: Possible SYN flooding on port 53. Sending cookies.  Check SNMP counters.
```

---

### Post by SeijiSensei on 2017-03-22
> DNS server 127.0.1.1

The server appears to be listening on 127.0.1.1, not 127.0.0.1.

You can control this using the [listen-on]("https://www.cyberciti.biz/faq/unix-linux-bsd-bind-dns-listenon-configuration/") directive in named.conf.  Watch those semicolons; they're critical.

---

### Post by MechaMechanism on 2017-03-23
> **SeijiSensei said:**
> The server appears to be listening on 127.0.1.1, not 127.0.0.1.

You can control this using the [listen-on]("https://www.cyberciti.biz/faq/unix-linux-bsd-bind-dns-listenon-configuration/") directive in named.conf.  Watch those semicolons; they're critical.

It doesn't matter which local address I use.  127.0.0.1 or 127.0.1.1 both fail.  I don't see any reason why 127.0.0.1 shouldn't work, that's how it's always worked.  I'm doing a v machine now to see if it's just me or endemic to 16.10.

```
sudo apt install bind9
```  Should just work as a caching server with no editing of files.  It's designed that way out of the box.

---

### Post by papibe on 2017-03-23
Hi MechaMechanism
> **MechaMechanism said:**
>  I installed Bind9 and made no alterations to the files in /etc or anywhere else.
> **MechaMechanism said:**
> ```
sudo apt install bind9
```  Should just work as a caching server with no editing of files.  It's designed that way out of the box.
Just to be sure, bind9 **does not work** out of the box without configuring it. Take a look this [tutorial]("https://help.ubuntu.com/community/BIND9ServerHowto"). I'd recommend setting up a [Caching Server]("https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server_configuration").

EDIT: here's another good tutorial: [How To Configure Bind as a Caching or Forwarding DNS Server on Ubuntu]("https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by MechaMechanism on 2017-03-23
The default install IS a caching server and does indeed work out of the box.  To quote the [https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server_configuration](https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server_configuration)

> Caching Server configuration

The default configuration is setup to act as a caching server.

All that is required is simply adding the IP numbers of your ISP's DNS servers.

Simply uncomment and edit the following in /etc/bind/named.conf.options:

        [...]

        forwarders {
             1.2.3.4;
             5.6.7.8;
        };

        [...]

(where 1.2.3.4 and 5.6.7.8 are the IP numbers of your ISP's DNS servers)

Now restart the bind daemon:

sudo /etc/init.d/bind9 restart

This imply that it works without any editing.  If you don't add your ISP DNS it simply contacts the root servers.  And I know it works this way because I have used bind for several years as a caching server.  It worked in 15.10 and then I purged it and now that I'm on 16.10 it don't work anymore.

I checked on a v machine.  It's a bug in Ubuntu.  [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1675221](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1675221)

Also that wiki is horribly out of date by many years.

Also this; ```
Mar 21 22:10:27 frontier kernel: [   79.504499] TCP: request_sock_TCP: Possible SYN flooding on port 53. Sending cookies.  Check SNMP counters.
```

---

### Post by MechaMechanism on 2017-03-23
To add I tested in 15.10 and the caching server worked out of the box.  Could not test 16.04.2 because of issues with Virtualbox.

See this bug report.  [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1675221](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1675221)

---

### Post by MechaMechanism on 2017-07-05
Works now.  I think it needed the following;
```
listen-on    { any; };
```
Why that's not included by default I don't know.  Started working as soon as I added the IPv4 in addition to the IPv6.

---

