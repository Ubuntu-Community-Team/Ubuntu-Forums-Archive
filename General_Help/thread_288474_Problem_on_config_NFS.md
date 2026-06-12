---
title: "Problem on config NFS"
date: 2006-10-29
forum: General Help
---

### Post by satimis on 2006-10-29
Hi folks,

Ubuntu-6.06.1-server-amd64
Broadband connection via ADSL modem --> telephone line
Dynamic IP addr.


I'm now configuring the server for test only and stuck on NFS
configuration.

$ cat /etc/hosts```

127.0.0.1	localhost	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

$ sudo /etc/init.d/nfs-kernel-server restart```

Stopping rpc mounted ... [ok] 
Stopping rpc rfsd ... [ok] 
Unexporting directories for NFS kernel daemon ... [ok]
Exporting directories of NFS kernel ademon ... [ok] 
Starting rpc rfsd .... [fail]

```

$ cat /var/log/syslog | grep nfs```

.....
......
Oct 30 00:29:24 ubuntu kernel: [   44.387818] Installing knfsd
(copyright 
(C) 1996 [email]okir@monad.swb.de[/email]).
Oct 30 00:29:25 ubuntu kernel: [   44.504583] NFSD: Using 
/var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Oct 30 00:29:25 ubuntu kernel: [   44.504598] NFSD: recovery directory 
/var/lib/nfs/v4recovery doesn't exist
Oct 30 00:29:25 ubuntu nfsd[4074]: nfssvc: Network is unreachable
Oct 30 00:29:26 ubuntu rpc.statd[4182]: statd running as root. chown 
/var/lib/nfs/sm to choose different user 
Oct 30 00:42:33 ubuntu kernel: [  832.835144] NFSD: Using 
/var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Oct 30 00:42:33 ubuntu kernel: [  832.835154] NFSD: recovery directory 
/var/lib/nfs/v4recovery doesn't exist
Oct 30 00:42:33 ubuntu nfsd[4427]: nfssvc: Network is unreachable

```

$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auth eth0
iface eth0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

Each time after booting PC, have to re-run "sudo pppoeconf" to make
broadband connection.  "sudo pon dsl-provider" does not work even no
complaint displayed.

Please help.  TIA

B.R.
satimis

---

