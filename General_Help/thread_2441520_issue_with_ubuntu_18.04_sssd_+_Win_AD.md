---
title: "issue with ubuntu 18.04 sssd + Win AD"
date: 2020-04-24
forum: General Help
---

### Post by anoharo on 2020-04-24
Hi,


I have to connect Ubuntu 18.04 with SSSD to a Windows AD.
We have lot's of other linux servers (mostly RHEL) with SSSD running so I thought I transfer the sssd.conf, do the necessary changes and I'm done.

Kerberos, nsswitch, pam.d, etc. are set up.


To check the transferred config I have run "sss_ctl config-check" which throw some errors and I fixed them except these:
```
Attribute 'ad_search_base' is not allowed in section 'domain/mydomain.sys'
Attribute 'ldap_sasl_realm' is not allowed in section 'domain/mydomain.sys'
Attribute 'ldap_user_member' is not allowed in section 'domain/mydomain.sys'
```


It seems that there is no equivalent for these in Ubuntu.


So I have disabled them and started sssd, but this is what I get in /var/log/sssd/sssd_mydomain.self.log:
```
[sbus_issue_request_done] (0x0040): sssd.dataprovider.getDomains: Error [1432158215]: DP target is not configured
[sbus_issue_request_done] (0x0040): sssd.dataprovider.getDomains: Error [1432158215]: DP target is not configured
[sbus_issue_request_done] (0x0040): sssd.dataprovider.getDomains: Error [1432158215]: DP target is not configured
```


I couldn't find anything related to this.

And when I try to log in with ssh, this is in the logs:
```
Group members are ignored, nothing to do. If you see this message it might indicate an error in the group processing logic.
sdap_ad_resolve_sids_done] (0x0020): Unable to resolve SID S-1-5-........... - will try next sid.
```



I'm out of ideas, any help is appreciated.

---

