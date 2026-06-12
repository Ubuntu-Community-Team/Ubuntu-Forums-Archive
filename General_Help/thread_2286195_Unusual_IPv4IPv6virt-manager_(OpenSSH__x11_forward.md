---
title: "Unusual IPv4/IPv6/virt-manager (OpenSSH / x11 forwarding) problem with work-around"
date: 2015-07-10
forum: General Help
---

### Post by Tazi on 2015-07-10
Hello .. just documenting this issue to help others who may be running into it.  In summary, virt-manager's x11 forwarding breaks when IPv6 is disabled on the server.  when I re-enable IPv6 on the "lo" interface, virt-manager's x11 functionality returns.  I'm a bit of an Ubuntu newbie, and have not had a chance to dig more deeply into the problem.

The work is for a client, and the client has some specific requirements.  The client is also unwilling to deviate from the requested configuration.

The base install is Ubuntu server 14.04 LTS with OpenSSH Server and Virtual Server host.  Installing with these packages installed as part of the initial set-up or manually adding them later does not matter.  Additional packages installed are virt-manager, virt-viewer, ifenslave-2.6 and of course bridge-utils (tested both pre-installed and manually added).  Order of install and configuration does not matter & has been tested.

The server has 3 on-board NICs, 1 for dedicated IMPI 2.0 (ignored by Ubuntu) and 2 for LAN use.  All NICs function normally.

When configuring networking, I have tested with a single NIC, a single bridged NIC, a bonded pair of NICs, and a bonded and bridged pair of NICs.  All basic networking scenarios worked correctly and functioned as expected.

The client manages these servers via OpenSSH and command line, but uses x11 forwarding to provide some GUI tools to make VM management easier.

The client also specifically requested that IPv6 be disabled on these servers.

The specific action that caused the failure:

IPv6 was disabled per the Ubuntu howto with the following lines added to /etc/sysctl.conf

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

The specific failure:

When the "virt-manager" command was issued, the x11 based GUI interface no longer functioned.  the pop-up window no longer appeared.

The work-around:

I fond that commenting out 2 of the 3 lines above re-enabled the local IPv6 ( lo ) interface, and allowed it to have an IPv6 address of ::1/128.  With local IPv6 functioning, virt-manager's x11 forwarding returned.  

The only IPv6 disable line I am currently running currently in /etc/sysctl.conf is:

net.ipv6.conf.default.disable_ipv6 = 1

This work-around has only been tested with a pair of bonded and bridged NICs, but does seem to restrict IPv6 traffic to the lo interface.  No other network interfaces are being given an IPv6 address.

---

### Post by Tazi on 2015-07-13
I assume the issues is caused by the how I was initially disabling IPv6 (per the how-to), and that there are still other "crumbs" of existing IPv6 configuration in other modules.  My concern is that if I had needed to have IPv6 fully disabled throughout the server (instead of just on the external NICs), there does not seem to be an official guide that goes beyond the how-to and really addresses the issue.

---

