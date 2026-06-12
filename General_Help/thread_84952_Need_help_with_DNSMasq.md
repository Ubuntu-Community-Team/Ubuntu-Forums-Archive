---
title: "Need help with DNSMasq"
date: 2005-11-01
forum: General Help
---

### Post by WebsterTrivium on 2005-11-01
This is running on an Ubuntu 5.10 box I just setup, with my other test machine as a Windows XP machine.

I'm trying to setup the Ubuntu machine as a DNS/DHCP server, to achieve plain name resolution for the machines on my lan.

I got DNSMasq downloaded and installed, and it's mostly working. When I look at IPConfig on my laptop, and the DNS/DHCP servers are pointed at the Ubuntu machine, and name resolution works great on the wan side, and my laptop has no problems getting out on the internet, but I'm unable to get name resolution for pinging the Ubuntu machine, nor can the Ubuntu machine ping the laptop by name.

Any help is greatly appreciated!!

My /etc/dnsmasq.conf file looks like this:

```
# Never forward plain names (with a dot or domain part)
domain-needed
# Never forward addresses in the non-routed address spaces.
bogus-priv

# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
filterwin2k

# set range of valid addressed for DHCP server
dhcp-range=192.168.10.200,192.168.10.225,12h

# default gateway
dhcp-option=3,192.168.10.77
```

My /etc/resolv.conf looks like:

```
nameserver 127.0.0.1
nameserver 166.102.165.11
nameserver 166.102.165.13

```

---

### Post by WebsterTrivium on 2005-11-01
Okay, I added the lines:

```
expand-hosts
domain=test.test

```

And I'm getting name resolution for plain names. One wierd thing that isn't a show-stopper, but I would like to figure out is, whenever any machine pings the Ubuntu Box (The DNS/DHCP server) by name, it returns 127.0.0.1

If anyone has any ideas, please let me know!

---

