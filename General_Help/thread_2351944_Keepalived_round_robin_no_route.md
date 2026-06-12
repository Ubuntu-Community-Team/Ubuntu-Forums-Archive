---
title: "Keepalived round robin no route"
date: 2017-02-08
forum: General Help
---

### Post by konrasko on 2017-02-08
Hi guys,
I have a very simple schema:

1 keepalivedHost -> round roubin two hosts

config below:

global_defs {
   notification_email {
       [email]konstantin@dot.com[/email]
   }
   notification_email_from [email]konstantin@dot.com[/email]
   smtp_server mailhost
   smtp_connect_timeout 30
}


vrrp_instance VirtIP_10 {
    state MASTER
    interface eth0
    virtual_router_id 100
! UNIQUE:
    priority 150
    advert_int 3
    smtp_alert
    authentication {
        auth_type PASS
        auth_pass MY_PASS
    }
    virtual_ipaddress {
        172.23.200.30
    }
}


virtual_server 172.23.200.30 80 {
    delay_loop 10
    lvs_sched wlc
    lvs_method DR
    persistence_timeout 5
    protocol TCP


    real_server 172.23.200.35 80 {
        weight 50
        TCP_CHECK {
            connect_timeout 3
        }
    }


    real_server 172.23.200.36 80 {
        weight 50
        TCP_CHECK {
            connect_timeout 3
        }
    }


}

if I do direct telnet to hosts on port 80 - everything works fine

But when I do telnet agains vip 172.23.200.30 80 - response is telnet: connect to address 172.23.200.30: No route to host

ip_forward = 1 on keepalived host

Any thoughts?

Thanks

---

