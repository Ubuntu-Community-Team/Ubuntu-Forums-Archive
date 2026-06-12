---
title: "Freeradius + AD"
date: 2014-01-31
forum: General Help
---

### Post by martinpedros on 2014-01-31
I set up a scenario of atuenticacion where I have a freeradius (Ubuntu 12.10) an active directory and a switch with 802.1x. I have a problem when the freeradius search a users in AD. Someone could help me to check the configuration of the LDAP module, I think the problem here is because both, the freeradius as AD, work well separately. The user defined to read users in the AD is "freeradius".

   I'm not sure if is necesary what the AD is present in the clients file or not?

================================================================

ldap {
        server = "ad_host.company.com.ar"
        identity = "cn=freeradius,dc=company,dc=com,dc=ar"
        password = password
        basedn = "dc=company,dc=com,dc=ar"
        filter = "(uid=%{%{Stripped-User-Name}:-%{User-Name}})"
        ldap_connections_number = 5
        timeout = 4
        timelimit = 3
        net_timeout = 1
        tls {
                start_tls = no
        }
        dictionary_mapping = ${confdir}/ldap.attrmap
        edir_account_policy_check = no
        keepalive {
                # LDAP_OPT_X_KEEPALIVE_IDLE
                idle = 60

                # LDAP_OPT_X_KEEPALIVE_PROBES
                probes = 3

                # LDAP_OPT_X_KEEPALIVE_INTERVAL
                interval = 3
        }
}

================================================================

Thanks,

---

