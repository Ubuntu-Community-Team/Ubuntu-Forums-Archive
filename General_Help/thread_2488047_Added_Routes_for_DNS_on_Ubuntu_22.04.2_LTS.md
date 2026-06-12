---
title: "Added Routes for DNS on Ubuntu 22.04.2 LTS"
date: 2023-06-21
forum: General Help
---

### Post by brettroderick on 2023-06-21
Problem occurring after:
-Ubuntu 22.04.2 LTS upgraded from Ubuntu 18.04.6 LTS
-Ubuntu 22.04.2 LTS upgraded from Ubuntu 20.04.6 LTS
 
Systems are:
--Ubuntu Servers are on Azure VM running OpenVPN Access Server
--Ubuntu Servers on physical servers running OpenVPN Client
 
Problem:
After upgrading to Ubuntu 22.04.2 LTS, Ubuntu is creating IP Routes for DNS Servers on different subnets breaking VPN routes.
 
Example:
Destination         Gateway               Genmask                    Flags      Metric   Ref            Use          Iface
8.8.8.8               92.168.222.2   255.255.255.255              UGH       100        0             0             enp1s0
192.168.111.4   192.168.222.2   255.255.255.255             UGH       100        0             0             enp1s0
 
As a workaround:
-I can remove DNS Servers from different subnets which resolves the problem.
-I can manually remove routes and the systems work correctly.
 
I tried to:
Edit all found network files and add:
[Network]
DNSDefaultRoute=false
 
This had no effect; routes are still added.
I need to disable this new feature. Any help would be grateful.

---

