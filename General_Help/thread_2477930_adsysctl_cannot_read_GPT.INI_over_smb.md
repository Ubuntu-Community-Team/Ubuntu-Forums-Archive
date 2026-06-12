---
title: "adsysctl cannot read GPT.INI over smb"
date: 2022-08-11
forum: General Help
---

### Post by ks-chrisu on 2022-08-11
Running a couple of Ubuntu 20.04 LTS Desktop instances in a Windows AD environment. Both are domain-joined, AD user logins work as intended, and Windows-hosted smb shares can be accessed using kerberos tickets. The problem I'm having is when running 'adsysctl update', the policy update fails in a manner similar to the following:

```

root@dev-01:/home/ad/devuser# adsysctl update -m -vv
INFO No configuration file: Config File "adsys" Not Found in "[/home/ad/devuser /root /etc]".
We will only use the defaults, env variables or flags.
DEBUG Connecting as [[116547:814960]]
DEBUG New request /service/UpdatePolicy
DEBUG Requesting with parameters: IsComputer: true, All: false, Target: dev-01, Krb5Cc:
DEBUG NormalizeTargetName for "dev-01", type "computer"
DEBUG Check if grpc request peer is authorized
DEBUG Authorized as being administrator
DEBUG GetPolicies for "dev-01", type "computer"
DEBUG Getting gpo list with arguments: "--objectclass computer ldap://mydc1.school.edu dev-01"
DEBUG GPO "One of Many GPOs" for "dev-01" available at "smb://school.edu/SysVol/echool.edu/Policies/{ABCDEF01-2345-6789-ABCD-EF0123456789}"
[snip]
DEBUG Analyzing "One of Many GPOs"
[snip]
INFO No assets directory with GPT.INI file found on AD, skipping assets download
ERROR Error from server: error while updating policy: can't get policies for "dev-01": can't download all gpos and assets: one or more error while fetching GPOs and assets: can't download "One of Many GPOs": can't check if One of Many GPOs needs refreshing: no GPT.INI file: cannot open smb://school.edu/sysvol/school.edu/Policies/{ABCDEF01-2345-6789-ABCD-EF0123456789}/GPT.INI: permission denied

```

Server-side, I found multiples of the following log entry which correlate strongly with adsys update attempts:
```

SMB Session Authentication Failure

Client Name: \\10.254.254.1
Client Address: 10.254.254.1:35464
User Name: 
Session ID: 0x1680C64000B11
Status: The request is not supported. (0xC00000BB)
SPN: session setup failed before the SPN could be queried
SPN Validation Policy: SPN optional / no validation

Guidance:

You should expect this error when attempting to connect to shares using incorrect credentials.

This error does not always indicate a problem with authorization, but mainly authentication. It is more common with non-Windows clients.

This error can occur when using incorrect usernames and passwords with NTLM, mismatched LmCompatibility settings between client and server, an incorrect service principal name, duplicate Kerberos service principal names, incorrect Kerberos ticket-granting service tickets, or Guest accounts without Guest access enabled

```

If I run 'adsys update' multiple times, each time it flags a different GPT.INI smb-hosted file as having the same issue. With enough repetitions, I was able to determine that adsys is unable to access the contents of any assigned GPO over smb. The odd thing is, the following test does work:

```

root@dev-01:/home/ad/devuser# mount.cifs "//school.edu/sysvol/school.edu/Policies/{ABCDEF01-2345-6789-ABCD-EF0123456789}" /mnt/smbtest0 -o sec=krb5i,ro
root@dev-01:/home/ad/devuser# ls /mnt/smbtest0
 Adm   GPT.INI  'Group Policy'   MACHINE   USER

```

SSSD appears to be in a healthy state, and we haven't had any issues with our current kerberos config. Similarly, server-side permissions for the affected group policy objects & their files are configured to permit read access by the machine accounts that computers dev-01 and dev-02 (my other Ubuntu test system) use. At this point I'm not sure whether this is a configuration issue or a bug of some sort (maybe golang implements smb + krb5 in an strange mannner?). Any input or recommendations would be appreciated.

/etc/sssd/sssd.conf
```

[sssd]
config_file_version = 2
domains = school.edu
default_domain_suffix = school.edu
services = ifp

[domain/school.edu]
access_provider = simple
ad_domain = school.edu
cache_credentials = True
default_shell = /bin/bash
default_shell = /bin/bash
dns_discovery_domain = SCHOOL.EDU
fallback_homedir = home/ad/%u
id_provider = ad
krb5_realm = SCHOOL.EDU
krb5_store_password_if_offline = True
ldap_id_mapping = True
override_homedir = /home/ad/%u
override_shell = /bin/bash
realmd_tags = manages-system joined-with-adcli
simple_allow_groups = AGroup01, AGroup02
simple_allow_users = ASvcAcct01

```

/etc/krb5.conf
```

[libdefaults]
        default_realm = SCHOOL.EDU
        dns_lookup_realm = true
        dns_lookup_kdc = true
        ticket_lifetime = 24h
        renew_lifetime = 7d
        rdns = false
        forwardable = true

[domain_realm]

```

---

