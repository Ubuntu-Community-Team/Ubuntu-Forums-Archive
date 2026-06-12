---
title: "Need some help configuring LDAP auth into Ubuntu desktops?"
date: 2022-08-28
forum: General Help
---

### Post by Surfrock66 on 2022-08-28
I've got an OpenLDAP server with its own TLS cert issued by my internal certificate authority.  The desktop clients have the CA installed, and the CA is referenced in /etc/ldap/ldap.conf as a "TLS_CACERT" on them.  ldapsearch works correctly on all of the clients with the -ZZ flag for forcing starttls.

As far as I can tell from reading, sssd is the recommended method of handling ldap login.  I've followed several guides, specifically:

[https://kifarunix.com/configure-sssd-for-ldap-authentication-on-ubuntu-20-04/](https://kifarunix.com/configure-sssd-for-ldap-authentication-on-ubuntu-20-04/)
[https://textbooks.cs.ksu.edu/cis527/4-directory-services/08-ubuntu-client-configuration/](https://textbooks.cs.ksu.edu/cis527/4-directory-services/08-ubuntu-client-configuration/)
[https://ubuntu.com/server/docs/service-sssd-ldap](https://ubuntu.com/server/docs/service-sssd-ldap)

Unfortunately, I'm not having success getting it to work.  Here is my sssd.conf, which is set to 600 perms:

```
# cat /etc/sssd/sssd.conf 
[sssd]
config_file_version = 2
debug_level=9
domains = SUBDOMAIN.DOMAIN.com

[nss]

[pam]
offline_credentials_expiration = 60

[domain/SUBDOMAIN.DOMAIN.com]
ldap_id_use_start_tls = True
cache_credentials = True
ldap_search_base = dc=SUBDOMAIN,dc=DOMAIN,dc=com
id_provider = ldap
auth_provider = ldap
enumerate = true
chpass_provider = ldap
access_provider = ldap
ldap_uri = ldap://SUBDOMAIN.DOMAIN.com
ldap_default_bind_dn = cn=ldapbinduser,ou=accounts,dc=SUBDOMAIN,dc=DOMAIN,dc=com
ldap_default_authtok = REDACTED
ldap_tls_reqcert = demand
ldap_tls_cacert = /etc/ssl/certs/SUBDOMAIN.DOMAIN.com.rootca.2032.08.24.pem
ldap_tls_cacertdir = /etc/ssl/certs
ldap_search_timeout = 50
ldap_network_timeout = 60
ldap_access_order = filter
ldap_access_filter = memberOf=cn=authorizedusers,ou=groups,dc=SUBDOMAIN,dc=DOMAIN,dc=com
```

```
# cat /etc/ldap/ldap.conf 
TLS_CACERT	/etc/ssl/certs/SUBDOMAIN.DOMAIN.com.rootca.2032.08.24.pem
```

When I restart the sssd service, I get an error and the following backtrace in the sssd logs:

```
(2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_rfc2307_autofs_defaults] (0x0010): Unable to read from confdb [2]: No such file or directory
********************** PREVIOUS MESSAGE WAS TRIGGERED BY THE FOLLOWING BACKTRACE:
   *  [be[SUBDOMAIN.DOMAIN.com]] [become_user] (0x0200): Trying to become user [0][0].
   *  [be[SUBDOMAIN.DOMAIN.com]] [become_user] (0x0200): Already user [0].
   *  [be[SUBDOMAIN.DOMAIN.com]] [ldb] (0x0400): server_sort:Unable to register control with rootdse!
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [server_setup] (0x0400): CONFDB: /var/lib/sss/db/config.ldb
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option lookup_family_order has value ipv4_first
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option dns_resolver_timeout has value 6
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option dns_resolver_op_timeout has value 3
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option dns_resolver_server_timeout has value 1000
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option dns_discovery_domain has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_res_get_opts] (0x0100): Lookup order: ipv4_first
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [recreate_ares_channel] (0x0100): Initializing new c-ares channel
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [fo_context_init] (0x0400): Created new fail over context, retry timeout is 30
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [confdb_get_domain_internal] (0x1000): pwd_expiration_warning is -1
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_domain_init_internal] (0x0200): DB File for SUBDOMAIN.DOMAIN.com: /var/lib/sss/db/cache_SUBDOMAIN.DOMAIN.com.ldb
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_domain_init_internal] (0x0200): Timestamp file for SUBDOMAIN.DOMAIN.com: /var/lib/sss/db/timestamps_SUBDOMAIN.DOMAIN.com.ldb
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_ldb_connect] (0x4000): No ldb module path set in env
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldb] (0x0400): asq: Unable to register control with rootdse!
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_ldb_connect] (0x4000): No ldb module path set in env
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sss_domain_get_state] (0x1000): Domain SUBDOMAIN.DOMAIN.com is Active
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sss_names_init_from_args] (0x0100): Using re [(?P<name>[^@]+)@?(?P<domain>[^@]*$)].
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sss_fqnames_init] (0x0100): Using fq format [%1$s@%2$s].
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_client_init] (0x0100): Set-up Backend ID timeout [0x561d9772c980]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [id]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [auth]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [access]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [chpass]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [sudo]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [autofs]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [selinux]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [hostid]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [subdomains]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [session]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_configuration] (0x0100): Using [ldap] provider for [resolver]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_init] (0x0400): Initializing target [id] with module [ldap]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_module] (0x0400): About to load module [ldap].
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_module_open_lib] (0x1000): Loading module [ldap] with path [/usr/lib/x86_64-linux-gnu/sssd/libsss_ldap.so]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_module_run_constructor] (0x0400): Executing module [ldap] constructor.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_uri has value ldap://SUBDOMAIN.DOMAIN.com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_backup_uri has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_search_base has value dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_default_bind_dn has value cn=ldapbinduser,ou=accounts,dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_default_authtok_type has value password
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_default_authtok has a binary value.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_search_timeout has value 50
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_network_timeout has value 60
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_opt_timeout has value 8
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_tls_reqcert has value demand
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_user_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_user_search_scope has value sub
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_user_search_filter has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_user_extra_attrs has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_group_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_group_search_scope has value sub
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_group_search_filter has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_host_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_service_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_full_refresh_interval has value 21600
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_smart_refresh_interval has value 900
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_random_offset has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_use_host_filter is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_hostnames has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_ip has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_include_netgroups is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sudo_include_regexp is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_autofs_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_autofs_map_master_name has value auto.master
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_iphost_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_ipnetwork_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_schema has value rfc2307
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_pwmodify_mode has value exop
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_offline_timeout has value 60
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_force_upper_case_realm is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_enumeration_refresh_timeout has value 300
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_purge_cache_timeout has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_tls_cacert has value /etc/ssl/certs/SUBDOMAIN.DOMAIN.com.rootca.2032.08.24.pem
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_tls_cacertdir has value /etc/ssl/certs
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_tls_cert has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_tls_key has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_tls_cipher_suite has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_id_use_start_tls is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_id_mapping is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sasl_mech has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sasl_authid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sasl_realm has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sasl_minssf has value -1
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sasl_maxssf has value -1
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_krb5_keytab has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_krb5_init_creds is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option krb5_server has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option krb5_backup_server has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option krb5_realm has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option krb5_canonicalize is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option krb5_use_kdcinfo is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option krb5_kdcinfo_lookahead has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_pwd_policy has value none
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_referrals is TRUE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option account_cache_expiration has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_dns_service_name has value ldap
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_krb5_ticket_lifetime has value 86400
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_access_filter has value memberOf=cn=authorizedusers,ou=groups,dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_netgroup_search_base has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_group_nesting_level has value 2
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_deref has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_account_expire_policy has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_access_order has value filter
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_chpass_uri has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_chpass_backup_uri has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_chpass_dns_service_name has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_chpass_update_last_change is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_enumeration_search_timeout has value 60
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_auth_disable_tls_never_use_in_production is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_page_size has value 1000
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_deref_threshold has value 10
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_sasl_canonicalize is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_connection_expire_timeout has value 900
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_connection_expire_offset has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_disable_paging is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_range_min has value 200000
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_range_max has value 2000200000
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_range_size has value 200000
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_autorid_compat is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_default_domain has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_default_domain_sid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_idmap_helper_table_size has value 10
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_use_tokengroups is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_rfc2307_fallback_to_local_users is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_disable_range_retrieval is FALSE
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_min_id has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_max_id has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_pwdlockout_dn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option wildcard_limit has value 1000
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_get_options] (0x0400): Option ldap_library_debug_level has value 0
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_user_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_group_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_netgroup_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_host_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_service_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_iphost_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_options] (0x0400): Option ldap_ipnetwork_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [DEFAULT][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [USER][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [GROUP][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [NETGROUP][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [HOST][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [SERVICE][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [IPHOST][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [IPNETWORK][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_rootdse_last_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_object_class has value posixAccount
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_name has value uid
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_pwd has value userPassword
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_uid_number has value uidNumber
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_gid_number has value gidNumber
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_gecos has value gecos
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_home_directory has value homeDirectory
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shell has value loginShell
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_principal has value krbPrincipalName
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_fullname has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_member_of has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_uuid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_objectsid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_primary_group has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_modify_timestamp has value modifyTimestamp
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_last_change has value shadowLastChange
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_min has value shadowMin
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_max has value shadowMax
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_warning has value shadowWarning
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_inactive has value shadowInactive
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_expire has value shadowExpire
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_shadow_flag has value shadowFlag
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_krb_last_pwd_change has value krbLastPwdChange
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_krb_password_expiration has value krbPasswordExpiration
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_pwd_attribute has value pwdAttribute
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_authorized_service has value authorizedService
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_ad_account_expires has value accountExpires
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_ad_user_account_control has value userAccountControl
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_ns_account_lock has value nsAccountLock
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_authorized_host has value host
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_authorized_rhost has value rhost
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_nds_login_disabled has value loginDisabled
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_nds_login_expiration_time has value loginExpirationTime
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_nds_login_allowed_time_map has value loginAllowedTimeMap
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_ssh_public_key has value sshPublicKey
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_auth_type has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_certificate has value userCertificate;binary
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_user_email has value mail
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_object_class has value posixGroup
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_object_class_alt has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_pwd has value userPassword
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_gid_number has value gidNumber
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_member has value memberuid
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_uuid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_objectsid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_modify_timestamp has value modifyTimestamp
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_type has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_group_external_member has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_netgroup_object_class has value nisNetgroup
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_netgroup_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_netgroup_member has value memberNisNetgroup
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_netgroup_triple has value nisNetgroupTriple
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_netgroup_modify_timestamp has value modifyTimestamp
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_object_class has value ipHost
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_fqdn has value fqdn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_serverhostname has value serverHostname
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_member_of has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_ssh_public_key has value sshPublicKey
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_host_uuid has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_service_object_class has value ipService
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_service_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_service_port has value ipServicePort
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_service_proto has value ipServiceProtocol
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_service_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_iphost_object_class has value ipHost
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_iphost_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_iphost_number has value ipHostNumber
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_iphost_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_ipnetwork_object_class has value ipNetwork
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_ipnetwork_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_ipnetwork_number has value ipNetworkNumber
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_ipnetwork_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [krb5_try_kdcip] (0x0100): No KDC found in configuration, trying legacy option
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [get_sdap_service] (0x0100): Service name for discovery set to ldap
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [fo_new_service] (0x0400): Creating new service 'LDAP'
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [_sdap_urls_init] (0x0400): Added URI ldap://SUBDOMAIN.DOMAIN.com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [fo_add_server_to_list] (0x0400): Inserted primary server 'SUBDOMAIN.DOMAIN.com:389' to service 'LDAP'
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_idmap_get_mappings] (0x4000): cn=id_mappings,cn=SUBDOMAIN.DOMAIN.com,cn=sysdb
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_idmap_get_mappings] (0x0080): Could not locate ID mappings: [No such file or directory]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_id_setup_tasks] (0x0400): Setting up enumeration for SUBDOMAIN.DOMAIN.com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_ptask_create] (0x0400): Periodic task [Enumeration [id] of SUBDOMAIN.DOMAIN.com] was created
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_ptask_schedule] (0x0400): Task [Enumeration [id] of SUBDOMAIN.DOMAIN.com]: scheduling task 10 seconds from now [1661643569]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_fo_set_srv_lookup_plugin] (0x0400): Trying to set SRV lookup plugin to DNS
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_fo_set_srv_lookup_plugin] (0x0400): SRV lookup plugin is now DNS
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_merge_res_ts_attrs] (0x2000): TS cache doesn't handle this DN type, skipping
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_delete_recursive_with_filter] (0x4000): Found [1] items to delete.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_delete_recursive_with_filter] (0x4000): Trying to delete [cn=certmap,cn=sysdb].
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sysdb_get_certmap] (0x0400): No certificate maps found.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_setup_certmap] (0x4000): No certmap data, nothing to do.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_run_constructor] (0x0400): Executing target [id] constructor
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_init] (0x0400): Initializing target [auth] with module [ldap]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_module] (0x0400): Module [ldap] is already loaded.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_run_constructor] (0x0400): Executing target [auth] constructor
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_init] (0x0400): Initializing target [access] with module [ldap]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_module] (0x0400): Module [ldap] is already loaded.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_run_constructor] (0x0400): Executing target [access] constructor
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_init] (0x0400): Initializing target [chpass] with module [ldap]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_module] (0x0400): Module [ldap] is already loaded.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_run_constructor] (0x0400): Executing target [chpass] constructor
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [init_chpass_service] (0x4000): ldap_chpass_uri and ldap_chpass_dns_service_name not set, using ldap_uri.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_init] (0x0400): Initializing target [sudo] with module [ldap]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_module] (0x0400): Module [ldap] is already loaded.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_run_constructor] (0x0400): Executing target [sudo] constructor
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sssm_ldap_sudo_init] (0x2000): Initializing LDAP sudo handler
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_sudo_init] (0x2000): Initializing sudo LDAP back end
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_sudo_options] (0x0200): Option ldap_sudo_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [common_parse_search_base] (0x0100): Search base added: [SUDO][dc=SUBDOMAIN,dc=DOMAIN,dc=com][SUBTREE][]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_object_class has value sudoRole
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_object_class_attr has value objectClass
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_name has value cn
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_command has value sudoCommand
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_host has value sudoHost
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_user has value sudoUser
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_option has value sudoOption
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_runas has value sudoRunAs
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_runasuser has value sudoRunAsUser
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_runasgroup has value sudoRunAsGroup
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_notbefore has value sudoNotBefore
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_notafter has value sudoNotAfter
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_order has value sudoOrder
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_get_map] (0x0400): Option ldap_sudorule_entry_usn has no value 
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_ptask_create] (0x0400): Periodic task [SUDO Full Refresh] was created
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_ptask_schedule] (0x0400): Task [SUDO Full Refresh]: scheduling task 10 seconds from now [1661643569]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_ptask_create] (0x0400): Periodic task [SUDO Smart Refresh] was created
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [be_ptask_schedule] (0x0400): Task [SUDO Smart Refresh]: scheduling task 910 seconds from now [1661644469]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_init] (0x0400): Initializing target [autofs] with module [ldap]
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_load_module] (0x0400): Module [ldap] is already loaded.
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [dp_target_run_constructor] (0x0400): Executing target [autofs] constructor
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sssm_ldap_autofs_init] (0x2000): Initializing LDAP autofs handler
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [sdap_autofs_init] (0x2000): Initializing autofs LDAP back end
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_get_autofs_options] (0x0200): Option ldap_autofs_search_base set to dc=SUBDOMAIN,dc=DOMAIN,dc=com
   *  (2022-08-27 16:39:19): [be[SUBDOMAIN.DOMAIN.com]] [ldap_rfc2307_autofs_defaults] (0x0010): Unable to read from confdb [2]: No such file or directory
********************** BACKTRACE DUMP ENDS HERE *********************************
```

I don't understand this autofs error.  My googling says that it can't read from a confDB file, but I can confirm it is there in the location I would expect it to be:

```
/var/lib/sss/db# ls -as1l
total 7544
   4 drwx------  2 root root    4096 Aug 18 09:49 .
   4 drwxr-xr-x 10 root root    4096 Aug 16 14:40 ..
1256 -rw-------  1 root root 1286144 Aug 18 09:47 cache_default.ldb
1256 -rw-------  1 root root 1286144 Aug 28 16:21 cache_SUBDOMAIN.DOMAIN.com.ldb
1256 -rw-------  1 root root 1286144 Aug 27 16:41 config.ldb
1256 -rw-------  1 root root 1286144 Aug 17 15:35 sssd.ldb
1256 -rw-------  1 root root 1286144 Aug 17 15:35 timestamps_default.ldb
1256 -rw-------  1 root root 1286144 Aug 18 09:49 timestamps_SUBDOMAIN.DOMAIN.com.ldb
```

This is over my understanding at this point, and any advice is needed.  Do I have a problem with my openLDAP config?  Is it an SSSD misconfiguration?  Is there a better system than SSSD for this, basic login using openLDAP usernames and passwords?

---

### Post by TheFu on 2022-08-29
autofs is completely separate from LDAP.  They aren't related, unless you make them related.  In the most common use of autofs + LDAP, it would be to automount user's HOME directories as needed from NFS storage.  With Ubuntu and their forced use of snap packages in all flavors, that won't work.  Snaps don't work under NFS or when home directories are in the exact location of 
/home/{username}

These do not work:
/u/{username}
/home/u1/{username}
/home/u2/{username}

This location is uncommon in corporations world-wide.  /home would be local storage for local users, typically server daemon accounts, not end users.  So, any snap packaged programs would fail to run.  Snaps are an inconvenient issue for corporations using LDAP and autofs for end user logins.  Very sad.

---

### Post by Surfrock66 on 2022-08-29
I'm not intentionally using autofs in any way, that is just straight out of the logs from sssd.  I wasn't sure if sssd is trying to mount something from the ldap server, but it didn't make much sense to me?

For this testing, this is a fresh install of Ubuntu Mate, I haven't even installed anything yet, it's like an hour old at the time of starting to configure LDAP.

---

