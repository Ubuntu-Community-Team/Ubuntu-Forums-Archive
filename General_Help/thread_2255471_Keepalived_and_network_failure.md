---
title: "Keepalived and network failure"
date: 2014-12-05
forum: General Help
---

### Post by ocset on 2014-12-05
Hi

I have been testing keepalived on two Ubuntu 14.04 machines and everything works fine when I shutdown/kill the primary machine but if I simply disconnect the network cable, fail-over never occurs. 

I have checked the log file and there are no new messages when I disconnect the network cable. 

Any suggestions

Thanks in advance
O.

---

### Post by nerdtron on 2014-12-05
Any chance on details how you setup keepalive? and how the network setup? We're basically blind on your situation here.

---

### Post by ocset on 2014-12-05
I have tried the following two test setups. 

1. Two virtual instances (virtual box) with their networks in bridge mode so they are getting an IP from a standard modem/router.

2. Two physical machines connected to a standard modem/router.

The /etc/keepalived/keepalived.conf file is the same on both machines:

```

! Configuration File for keepalived

vrrp_instance VI_1 {
    state EQUAL
    interface eth0
    virtual_router_id 51
    priority 100
    advert_int 1
    authentication {
        auth_type PASS
        auth_pass pass123
    }
    virtual_ipaddress {
        192.168.0.123
    }
}


```



Thanks in advance

---

