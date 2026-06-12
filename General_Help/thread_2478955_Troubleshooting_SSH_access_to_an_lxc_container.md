---
title: "Troubleshooting SSH access to an lxc container"
date: 2022-09-09
forum: General Help
---

### Post by veedub67 on 2022-09-09
Hello,

I am playing around with LXC containers for the first time.

I have setup a container running 22.04

I have enabled SSH on the container and opened port 22 on UFW in the container.

I can ping and ssh to the container from the container host.

I can ping the container from an external host, but cannot connect via SSH. There are no SSH diagnostics, port 22 appears to be closed, even though UFW says that it is allowed from ANYWHERE in the container.

I can SSH to the container host.

Am after suggestions on possible issues, things to try.

Thanks

VW

---

### Post by veedub67 on 2022-09-09
Hello,

I've done some further reading and am wondering whether the 'answer' might have something to do with creating a network forward

e.g. ```
lxc network forward create
```

I've since had a go at trying to create a network forward without success. So before I spent more time trying to resolve the error messages which I don't understand; hopefully someone can tell me if I'm on the right track or not.

Also wanted to mention that the lxc host is a Hyper-V VM; in case that is relevant here. I have read some comments about needing to enable promiscuous mode on the NIC when using a VM; although I can't see an option for that with Hyper-V.

---

### Post by TheFu on 2022-09-10
Are you using LXD to manage the LXC containers?
Did you tell lxd to connect the container to a bridge?
I've never setup forwarding into a container. I've been using bridged networking for my lxd containers.

---

### Post by veedub67 on 2022-09-10
> **TheFu said:**
> Are you using LXD to manage the LXC containers?
I'm not sure how to answer that. I'm not entirely clear on the difference between LXC and LXC.

I used ```
lxd init
``` to setup the environment.

```
lxd init --dump
config:
  core.https_address: '[::]:8443'
  core.trust_password: true
networks:
- config:
    ipv4.address: 10.244.32.1/24
    ipv4.nat: "true"
    ipv6.address: fd42:127a:eb4b:75ef::1/64
    ipv6.nat: "true"
  description: ""
  name: lxdbr0
  type: bridge
  project: default
storage_pools:
- config:
    source: /var/snap/lxd/common/lxd/storage-pools/default
  description: ""
  name: default
  driver: dir
profiles:
- config: {}
  description: Ubuntu LXD profile
  devices:
    eth0:
      name: eth0
      network: lxdbr0
      type: nic
    root:
      path: /
      pool: default
      type: disk
  name: Ubuntu
- config: {}
  description: Default LXD profile
  devices:
    eth0:
      name: eth0
      network: lxdbr0
      type: nic
    root:
      path: /
      pool: default
      type: disk
  name: default
projects:
- config:
    features.images: "true"
    features.networks: "true"
    features.profiles: "true"
    features.storage.buckets: "true"
    features.storage.volumes: "true"
  description: Default LXD project
  name: default

```

All the other commands that I have used have been: lxc

> Did you tell lxd to connect the container to a bridge?
```
$ lxc network list+--------+----------+---------+----------------+---------------------------+-------------+---------+---------+
|  NAME  |   TYPE   | MANAGED |      IPV4      |           IPV6            | DESCRIPTION | USED BY |  STATE  |
+--------+----------+---------+----------------+---------------------------+-------------+---------+---------+
| eth0   | physical | NO      |                |                           |             | 0       |         |
+--------+----------+---------+----------------+---------------------------+-------------+---------+---------+
| lxdbr0 | bridge   | YES     | 10.244.32.1/24 | fd42:127a:eb4b:75ef::1/64 |             | 3       | CREATED |
+--------+----------+---------+----------------+---------------------------+-------------+---------+---------+

```

I configured the static IP address for the container using
```

lxc stop Ubuntu
lxc network attach lxdbr0 Ubuntu eth0 eth0
lxc config device set Ubuntu eth0 ipv4.address 10.244.32.2
lxc start Ubuntu
```

---

### Post by veedub67 on 2022-09-10
The routing looks to be correct

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.244.32.1     0.0.0.0         UG    100    0        0 eth0
10.244.32.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0
10.244.32.1     0.0.0.0         255.255.255.255 UH    100    0        0 eth0

```

---

### Post by TheFu on 2022-09-10
Are the other systems on 10.244.32.1/24?

Did you install "ssh" or openssh-server packages?  
If you do an nmap scan of the IP from outside, is the port for ssh there?

---

### Post by veedub67 on 2022-09-10
> **TheFu said:**
> Are the other systems on 10.244.32.1/24?
Just the one container.

> Did you install "ssh" or openssh-server packages?
open-ssh-server

```
# sudo systemctl status ssh&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: e>
     Active: active (running) since Fri 2022-09-09 23:21:47 UTC; 1 day 4h ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 201 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 232 (sshd)
      Tasks: 1 (limit: 4547)
     Memory: 6.7M
        CPU: 98ms
     CGroup: /system.slice/ssh.service
             &#9492;&#9472;232 "sshd: /usr/sbin/sshd -D 
[listener] 0 of 10-100 startups"


Sep 09 23:21:47 Ubuntu systemd[1]: Starting OpenBSD Secure Shell server...
Sep 09 23:21:47 Ubuntu sshd[232]: Server listening on 0.0.0.0 port 22.
Sep 09 23:21:47 Ubuntu sshd[232]: Server listening on :: port 22.
Sep 09 23:21:47 Ubuntu systemd[1]: Started OpenBSD Secure Shell server.
Sep 10 00:33:41 Ubuntu sshd[563]: Accepted publickey for root from 10.244.3>
Sep 10 00:33:41 Ubuntu sshd[563]: pam_unix(sshd:session): session opened fo>
Sep 10 00:53:16 Ubuntu sshd[646]: Accepted publickey for root from 10.244.3>
Sep 10 00:53:16 Ubuntu sshd[646]: pam_unix(sshd:session): session opened fo>
Sep 10 23:55:38 Ubuntu sshd[1488]: Accepted publickey for root from 10.244.>
Sep 10 23:55:38 Ubuntu sshd[1488]: pam_unix(sshd:session): session opened f>

```

> If you do an nmap scan of the IP from outside, is the port for ssh there?

No. The host is detected as "UP" (i.e. responds to ICMP, but SSH is not detected).

I think I will install some other services like maybe a Web server and then see if that is accessible to try and narrow down the issue.

There is a router between the container host and the rest of the network, but there are rules in place for SSH. However I might also try making those rules more "open" to see if somehow there is an issue with the current configuration.

It is puzzling. 

At least I now know that I haven't missed a basic step in setting up the container.

---

### Post by TheFu on 2022-09-11
With only 1 container on a single subnet, that's pretty useless.  Sorta like the "host-only" networking provided by virtualbox.

If the containers aren't on the same subnet as the systems trying to access them, you'll have to setup specific routes on every network device to get the traffic there.  I put my containers on the same LAN as the other systems on that LAN ... my setup is a bit complex because I run multiple physically separate LANs as different security zones.  Within the same zone, all systems can use ethernet to find each other and don't need routing.

In a simple 1-subnet network with 1 LAN, the bridged networking should be on the same subnet as all other systems.  This is how I started out with my network 20+ yrs ago.

---

### Post by veedub67 on 2022-09-11
> **TheFu said:**
> In a simple 1-subnet network with 1 LAN, the bridged networking should be on the same subnet as all other systems.

That was a good suggestion. Thanks.

Unfortunately while I can access the container from the container host, I still can't access the container from other hosts.

I have reconfigured lxdbr0 onto the same subnet as the container host

```

lxc network list
+--------+----------+---------+------------------+---------------------------+-------------+---------+---------+
|  NAME  |   TYPE   | MANAGED |       IPV4       |           IPV6            | DESCRIPTION | USED BY |  STATE  |
+--------+----------+---------+------------------+---------------------------+-------------+---------+---------+
| eth0   | physical | NO      |                  |                           |             | 0       |         |
+--------+----------+---------+------------------+---------------------------+-------------+---------+---------+
| lxdbr0 | bridge   | YES     | 10.254.247.10/24 | fd42:127a:eb4b:75ef::1/64 |             | 3       | CREATED |
+--------+----------+---------+------------------+---------------------------+-------------+---------+---------+

```

I can ping 10.254.247.10 from both the container host and other internal hosts.

However I can't ping the container 10.254.247.70

For example, I have an internal host 10.254.242.100

It can ping the container host
```

tracert 10.254.247.85


Tracing route to 10.254.247.85 over a maximum of 30 hops


  1    <1 ms    <1 ms    <1 ms  10.254.242.1
  2    <1 ms    <1 ms    <1 ms  10.254.242.90
  3    <1 ms    <1 ms    <1 ms  10.254.247.85


Trace complete
```

It can also ping lxdbr0
```

tracert 10.254.247.10


Tracing route to 10.254.247.10 over a maximum of 30 hops


  1    <1 ms    <1 ms    <1 ms  10.254.242.1
  2    <1 ms    <1 ms    <1 ms  10.254.242.90
  3    <1 ms    <1 ms    <1 ms  10.254.247.10


Trace complete.
```

But the container is not reachable
```

tracert 10.254.247.70


Tracing route to 10.254.247.70 over a maximum of 30 hops


  1    <1 ms    <1 ms    <1 ms  10.254.242.1
  2     1 ms     1 ms    <1 ms  10.254.242.90
  3  10.254.242.90  reports: Destination host unreachable.


Trace complete.
```

The container however, can ping out
```

traceroute 10.254.242.100
traceroute to 10.254.242.100 (10.254.242.100), 30 hops max, 60 byte packets
 1  _gateway.lxd (10.254.247.10)  0.028 ms  0.011 ms  0.008 ms
 2  _gateway (10.254.247.90)  0.605 ms  0.576 ms  0.552 ms
 3  * * *
 4  * 10.254.242.100 (10.254.242.100)  0.897 ms *

```

It is as if the container is firewalled, but my understanding is that icmp is not blocked by default. And the only configuration I have made to ufw is to allow SSH.

---

### Post by TheFu on 2022-09-11
Going 1 direction means that route is fine.
Going back and failing means the routing is wrong.

ufw is generally configured with a default DENY setup and allowing ssh only allows .... ssh. Nothing else, including ping.

In short, I think you have a network and/or firewall problem, not an ssh issue.

---

### Post by veedub67 on 2022-09-12
@TheFu

It is helpful to have someone to chat to while troubleshooting. I appreciate your help.

I've done some further work and found two errors


[LIST=1]
[*]To allow ICMP through UFW you need to edit the before.rules config file. I have now done this
[*]For ping to reach the container host, the route to the container host needs to be the bridge IP address, this is obvious in retrospect.
[/LIST]

So I can now ping the container from an external host.

Unfortunately SSH is still not working from an external host, it does work from the container host.

To troubleshoot I've done a packet trace on the SSH connection attempt and while there are packets from the remote host, there are no replies from the container.

As the ping now works in both directions, I know that the routing is correct.

To try and isolate the issue to either the container or the router/firewall, I created two rules on the firewall. 

One to allow all traffic from the host to the container
One to allow all traffic from the container to the host

When I attempt an SSH connection. The packet count on the first rule increases, but there are no hits on the second rule.

That suggests to me that the container is not responding to the SSH connection attempt from any host other than the container host.

Any thoughts on how to troubleshoot this?

---

### Post by veedub67 on 2022-09-12
Decided to try the "nuclear option" and re-run lxd init

I created a new bridge.

Had a few issues getting an IPv4 address assigned to the container, but eventually resolved this.

Unfortunately no change, can ping from external hosts but not SSH. :-(

I think I will try creating a new container tomorrow. If that works, at least I can move on.

---

### Post by TheFu on 2022-09-12
I think the issue is your network design.  The bridge setup. Seems it is following the Docker method, not the Linux Bridge method.

Network stuff on my lxd host doesn't impact what the bridge to the containers see.  I'm actually using the same bridge for VMs and the containers on that same subnet running on the same physical host.  Well, this isn't technically true, but close enough for discussion here.

My lxd containers are just like every other system on the same subnet, including physical systems.  I stopped using the automatic bridges created by libvirt or lxd back in 2010.  At the time, the performance was terrible and a manual bridge was the solution to achieve the expected bandwidth. Host-only bridges are useless for my needs, which is usually running network services in the containers.  

I think ufw capabilities are limited to simple block/allow/limit rules.  For more complex rules, use iptables or nftables.  I could be wrong, but I've never looked to closely. UFW trades complete features for simplicity.
[https://www.cyberciti.biz/faq/how-to-configure-ufw-to-forward-port-80443-to-internal-server-hosted-on-lan/](https://www.cyberciti.biz/faq/how-to-configure-ufw-to-forward-port-80443-to-internal-server-hosted-on-lan/) has an explanation. Seems easier to just setup iptables.

---

### Post by veedub67 on 2022-09-13
@TheFu

Thanks for the link, that was helpful.

Eventually worked out that the answer was

```
lxc config device add Ubuntu ssh-redirect proxy listen=tcp:10.254.247.85:2222 connect=tcp:10.254.247.70:22
```

---

