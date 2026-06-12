---
title: "How to set static IP address for LXC container"
date: 2022-09-08
forum: General Help
---

### Post by veedub67 on 2022-09-08
Hello,

I'm trying to assign a static IP address to an LXC container.

The container image is: 22.04

From reading, my understanding is that the file /etc/network/interfaces in the container needs to be configured with the following info

```

auto eth0
iface eth0 inet static
address 10.244.32.2
netmask 255.255.255.0
gateway 10.244.32.1
dns-nameservers 8.8.8.8

```

I have done that, but the IP address is still being assigned by DHCP.

After suggestions on how to troubleshoot.

Thanks

VW

---

### Post by veedub67 on 2022-09-08
Hello,

I read a number of articles on this topic, with different approaches, none of which worked for me.

Eventually found this article [https://discuss.linuxcontainers.org/t/best-practices-for-assigning-static-ip-address/4012/2](https://discuss.linuxcontainers.org/t/best-practices-for-assigning-static-ip-address/4012/2)

Which described this approach, which did work

```

lxc stop c1
lxc network attach lxdbr0 c1 eth0 eth0
lxc config device set c1 eth0 ipv4.address 10.99.10.42
lxc start c1

```

---

### Post by TheFu on 2022-09-08
/etc/network/interfaces was deprecated around 2018.

I don't use LXC containers directly, but with LXD, setting up the static IP for each container is something I address inside the container using netplan config files. I suppose a DHCP reservation from an external DHCP server could be used, but I consider that a terrible idea.  Devices that don't move should be self-configured for static IPs, if there is a method for that.  Exceptions are laptops, streaming devices, network TV tuners, smart phones ... things that move between different networks or simply don't have a method to set a static IP.  Anything that is a "server" (provides a network service of any sort), should have an internally setup static IP. Period.
```

lxc profile list
lxc profile create bridged # name of profile is "bridged"
lxc launch -p default -p bridged ubuntu br9

```
Sorry, the advanced editor hasn't been working for me in months, so I cannot color code which parts connect.

---

