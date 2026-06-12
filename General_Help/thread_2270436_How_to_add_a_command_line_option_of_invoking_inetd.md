---
title: "How to add a command line option of invoking inetd?"
date: 2015-03-23
forum: General Help
---

### Post by Biao on 2015-03-23
I am running ubuntu12.04LTS.
I need to add a command line option to inetd invoking(like /usr/sbin/inetd -l -d ). Someone told me it is /etc/init.d/openbsd-inetd. but i am not sure where to add the "-l" in this file.
Were is the inetd invoked? and how to add the "-l" to the invoking?

Thanks in advance.
Jerry

---

### Post by Lars Noodén on 2015-03-23
1) Which inetd package do you have installed in 12.04?

```

dpkg -l '*inetd*'

```

The one installed will have an 'ii' in the leftmost column.

2) Why are you planning to add those switches to inetd?  What is the goal?  The [-l option](http://manpages.ubuntu.com/manpages/precise/en/man8/inetd.8.html) only turns on tcpwrapper support and much of that functionality is filled by iptables these days.  And the -d debug option will prevent it from running in the background.  Also, xinetd has much more functionality in regards to connection logging than inetd.   


3) But that aside, if you want to add the options -l -d to inetd when it runs, and you are using the package openbsd-inetd, then the file to edit is */etc/init.d/openbsd-inetd* and you want to add the line

OPTIONS="-l -d"

right after the line

DAEMON=/usr/sbin/inetd

---

### Post by Biao on 2015-03-23
> **Lars Noodén said:**
> 1) Which inetd package do you have installed in 12.04?

```

dpkg -l '*inetd*'

```

The one installed will have an 'ii' in the leftmost column.

2) Why are you planning to add those switches to inetd?  What is the goal?  The [-l option]("http://manpages.ubuntu.com/manpages/precise/en/man8/inetd.8.html") only turns on tcpwrapper support and much of that functionality is filled by iptables these days.  And the -d debug option will prevent it from running in the background.  Also, xinetd has much more functionality in regards to connection logging than inetd.   


3) But that aside, if you want to add the options -l -d to inetd when it runs, and you are using the package openbsd-inetd, then the file to edit is */etc/init.d/openbsd-inetd* and you want to add the line

OPTIONS="-l -d"

right after the line

DAEMON=/usr/sbin/inetd

Firstly thanks for your reply.
I just came to realize that i was on the wrong way.
My "goal" is to install a BOOTP server on my ubuntu12.04 host to serve my DevBoard's bring up, which require the BOOTP/DHCP protocol.

My router provides the DHCP service, so i think installing a BOOTP on my host will suffice, is it right? or BOOTP and DHCP should be running on the same host?
After installing the bootp pakcage, i did not found any document describing how should it be working with xinetd, can you give me a hint or reference?
So i would like to  change my question to that how to install and configure a BOOTP server on ubuntu-12.04 host.

Looking forward to your help.
Kindly Thanks again.

Jerry

---

### Post by Biao on 2015-03-23
It seems that the DHCP provides the BOOTP service, maybe i should install the DHCP and configure it with BOOTP enabled.

---

### Post by Lars Noodén on 2015-03-23
> **Biao said:**
> It seems that the DHCP provides the BOOTP service, maybe i should install the DHCP and configure it with BOOTP enabled.

Ubuntu 12.04 LTS comes with [dnsmasq](http://manpages.ubuntu.com/manpages/precise/en/man8/dnsmasq.8.html) (a DHCP server) already installed and running.  You can your customizations by adding a file to /etc/NetworkManager/dnsmasq.d/ with your changes to make it serve DHCP.  However, I'm not sure how it's going to mix with your router's existing DHCP service.  

If you are trying to do a PXE installation on your other device, dnsmasq also has a built-in tftp server, which would be one of the extra steps needed.

---

### Post by Biao on 2015-03-23
> **Lars Noodén said:**
> Ubuntu 12.04 LTS comes with [dnsmasq]("http://manpages.ubuntu.com/manpages/precise/en/man8/dnsmasq.8.html") (a DHCP server) already installed and running.  You can your customizations by adding a file to /etc/NetworkManager/dnsmasq.d/ with your changes to make it serve DHCP.  However, I'm not sure how it's going to mix with your router's existing DHCP service.  

If you are trying to do a PXE installation on your other device, dnsmasq also has a built-in tftp server, which would be one of the extra steps needed.
Now i got it. i would try to install the DHCP server with BOOTP enabled.

Thanks for your kindly help.

---

