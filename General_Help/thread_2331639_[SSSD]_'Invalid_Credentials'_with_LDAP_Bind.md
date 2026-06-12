---
title: "[SSSD] 'Invalid Credentials' with LDAP Bind"
date: 2016-07-24
forum: General Help
---

### Post by elegant2 on 2016-07-24
Hi guys,

I'm trying to get SSSD working on my Samba4 DC but I've hit an snap where the SASL bind won't bind to LDAP. It easily does a kinit with DC01$ (klist confirms it) but then when it attempts to bind it using SASL it fails.

Below is the log from SSSD:
```
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_kinit_send] (0x0400): Attempting kinit (default, DC01$, EXAMPLE.COM, 86400)(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_kinit_next_kdc] (0x1000): Resolving next KDC for service AD
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [fo_resolve_service_send] (0x0100): Trying to resolve service 'AD'
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [get_server_status] (0x1000): Status of server 'dc01.example.com' is 'name resolved'
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [fo_resolve_service_activate_timeout] (0x2000): Resolve timeout set to 6 seconds
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [get_server_status] (0x1000): Status of server 'dc01.example.com' is 'name resolved'
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [be_resolve_server_process] (0x1000): Saving the first resolved server
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [be_resolve_server_process] (0x0200): Found address for server dc01.example.com: [10.0.0.20] TTL 884
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_kinit_kdc_resolved] (0x1000): KDC resolved, attempting to get TGT...
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [create_tgt_req_send_buffer] (0x0400): buffer size: 45
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [child_handler_setup] (0x2000): Setting up signal handler up for pid [14505]
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [child_handler_setup] (0x2000): Signal handler set up for pid [14505]
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [set_tgt_child_timeout] (0x0400): Setting 6 seconds timeout for tgt child
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_process_result] (0x2000): Trace: sh[0x1572520], connected[1], ops[(nil)], ldap[0x1571080]
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_process_result] (0x2000): Trace: ldap_result found nothing!
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [write_pipe_handler] (0x0400): All data has been sent!
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [read_pipe_handler] (0x0400): EOF received, client finished
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_get_tgt_recv] (0x0400): Child responded: 0 [FILE:/var/lib/sss/db/ccache_EXAMPLE.COM], expired on [1469376752]
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_cli_auth_step] (0x0100): expire timeout is 900
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sdap_cli_auth_step] (0x1000): the connection will expire at 1469341652
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sasl_bind_send] (0x0100): Executing sasl bind mech: gssapi, user: DC01$
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sasl_bind_send] (0x0020): ldap_sasl_bind failed (49)[Invalid credentials]
(Sun Jul 24 02:12:32 2016) [sssd[be[example.com]]] [sasl_bind_send] (0x0080): Extended failure message: [SASL:[GSSAPI]: NT_STATUS_LOGON_FAILURE]
```

These are settings used by SSSD:
```


[sssd]
domains = example.com
config_file_version = 2
services = nss, pam


[domain/gaia-project.net]
debug_level = 9
ad_domain = example.com
ad_server = dc01.example.com
krb5_realm = EXAMPLE.COM
realmd_tags = manages-system joined-with-adcli 
cache_credentials = True
id_provider = ad
krb5_store_password_if_offline = True
default_shell = /bin/bash
ldap_id_mapping = True
use_fully_qualified_names = False
fallback_homedir = /home/%d/%u
access_provider = ad
```

Any info as to why it fails with LDAP would be greatly appreciated!

---

