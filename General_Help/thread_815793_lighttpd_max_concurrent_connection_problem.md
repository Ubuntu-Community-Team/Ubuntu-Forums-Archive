---
title: "lighttpd max concurrent connection problem"
date: 2008-06-02
forum: General Help
---

### Post by ikkubus on 2008-06-02
hi, i got a filehosting website and im having problem with concurrent connection. when i upload 2 files  simultaneously i cant open new page. but if i upload only one file i can still open new pages, do you have any idea how to fix this??
 thanks in advance

this is my lighttpd config

```

server.max-keep-alive-idle = 4
server.max-read-idle = 3600
server.max-write-idle = 3600

server.max-fds = 4096
server.max-connections = 2048

net.ipv4.tcp_fin_timeout = 1
net.ipv4.tcp_tw_recycle = 1

net.core.rmem_max = 16777216
net.core.rmem_default = 16777216
net.core.netdev_max_backlog = 262144
net.core.somaxconn = 262144

net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_syn_backlog = 262144

net.core.somaxconn = 262144

net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_max_orphans = 262144
net.ipv4.tcp_max_syn_backlog = 262144
net.ipv4.tcp_synack_retries = 2
net.ipv4.tcp_syn_retries = 2

net.ipv4.netfilter.ip_conntrack_max = 1048576
net.nf_conntrack_max = 1048576
evasive.max-conns-per-ip = 5


```

---

