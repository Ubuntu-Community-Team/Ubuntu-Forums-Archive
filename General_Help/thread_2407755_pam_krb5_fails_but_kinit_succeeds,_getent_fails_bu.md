---
title: "pam_krb5 fails but kinit succeeds, getent fails but ldapsearch succeeds"
date: 2018-12-08
forum: General Help
---

### Post by martycombs on 2018-12-08
Please forgive me if I am overlooking the answer to this question but I have searched multiple forums but cannot find the solution.

I am trying to replace an Ubuntu 14.04 AWS instance with an Ubuntu 18.04 instance.  The original successfully used kerberos through PAM to authenticate against Active Directory for ssh and LDAPS for NSS.  I have transferred the same configs from the older 14.04 instance to the newer 18.04 instance.


I have tried tweaking settings in configuration files, ran tcpdumps, netcat to confirm nothin is being blocked, etc but I have reached the limit of my troubleshooting ability.

Scenario:
[LIST]
[*] Both domain controller and ubuntu client are AWS instances.
[*] This used to work when the client instance ran Ubunut 14.04.
[*] Security groups allow full UDP and TCP connectivity between domain controller and client.  I have confirmed with netcat that connections succeed.
[*] I have increased the logging for sshd to DEBUG but cannot determine what is failing.
[*] Ssh to the new instance fails for a user, yet 'kinit' succeeds using the exact same password.
[*] A 'getent passwd $USER' returns nothing yet an ldapsearch for the same user succeeds.
[*] I do not want to use sssd.  I'm not joining this to a domain. I don't want to go into details why not.
[/LIST]

Snippet of /var/log/auth.log for an ssh attempt where kinit works.
```

Dec  8 23:21:35 ric01-pbkupv02 sshd[10358]: debug1: userauth-request for user mcombs service ssh-connection method password [preauth]
Dec  8 23:21:35 ric01-pbkupv02 sshd[10358]: debug1: attempt 3 failures 2 [preauth]
Dec  8 23:21:35 ric01-pbkupv02 sshd[10358]: pam_krb5(sshd:auth): authentication failure; logname=mcombs uid=0 euid=0 tty=ssh ruser= rhost=10.250.24.68
Dec  8 23:21:35 ric01-pbkupv02 sshd[10358]: pam_unix(sshd:auth): check pass; user unknown
Dec  8 23:21:35 ric01-pbkupv02 sshd[10358]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.250.24.68
Dec  8 23:21:35 ric01-pbkupv02 sshd[10358]: pam_ldap: error trying to bind as user "CN=Marty Combs,OU=Employees,OU=Users,OU=SFO03,OU=US,OU=NA,OU=Locations,DC=locusdev,DC=net" (Invalid credentials)
Dec  8 23:21:37 ric01-pbkupv02 sshd[10358]: debug1: PAM: password authentication failed for an illegal user: Authentication failure
Dec  8 23:21:37 ric01-pbkupv02 sshd[10358]: Failed password for invalid user mcombs from 10.250.24.68 port 54405 ssh2
Dec  8 23:21:38 ric01-pbkupv02 sshd[10358]: Connection closed by invalid user mcombs 10.250.24.68 port 54405 [preauth]

# kinit mcombs
Password for mcombs@LOCUSDEV.NET:

# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: mcombs@LOCUSDEV.NET

Valid starting     Expires            Service principal
12/08/18 23:24:03  12/09/18 09:24:03  krbtgt/LOCUSDEV.NET@LOCUSDEV.NET
        renew until 12/09/18 23:23:59

```

Another snippet where getent fails but ldapsearch succeeds.
```

# getent passwd mcombs
#

# ldapsearch -H ldaps://ad1-ric.locusdev.net:3269 -D "cn=svc binddn,cn=users,dc=locusdev,dc=net" -w "${BINDPW}" -b ou=locations,dc=locusdev,dc=net sAMAccountname=mcombs | tail
gidNumber: 2000
unixHomeDirectory: /locus/home/mcombs
loginShell: /bin/bash

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
#

```


Relevant options for configs are below.

/etc/ssh/sshd_config
```
PasswordAuthentication yes
ChallengeResponseAuthentication no
UsePAM yes
```

/etc/krb5.conf
```

[libdefaults]
  default_realm = LOCUSDEV.NET
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true

[realms]
        LOCUSDEV.NET = {
                kdc = ad1-ric.locusdev.net:88
                kdc = ad2-ric.locusdev.net:88
        }

[login]
        krb4_convert = false
        krb4_get_tickets = false

```

/etc/pam.d/sshd
```

@include common-auth
@include common-account
@include common-session
@include common-password
```

/etc/pam.d/common-auth:
```

auth    [success=3 default=ignore]      pam_krb5.so minimum_uid=1000
auth    [success=2 default=ignore]      pam_unix.so nullok_secure try_first_pass
auth    [success=1 default=ignore]      pam_ldap.so use_first_pass
auth    requisite                       pam_deny.so
auth    required                        pam_permit.so
auth    optional                        pam_cap.so

```

/etc/pam.d/common-account
```

account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so
account [success=1 default=ignore]      pam_ldap.so
account requisite                       pam_deny.so
account required                        pam_permit.so
account required                        pam_krb5.so minimum_uid=1000

```

/etc/pam.d/common-session
```

session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session optional                        pam_umask.so
session optional                        pam_krb5.so minimum_uid=1000
session required        pam_unix.so
session optional                        pam_ldap.so
session optional        pam_systemd.so

```

/etc/pam.d/common-password
```

password        [success=3 default=ignore]      pam_krb5.so minimum_uid=1000
password        [success=2 default=ignore]      pam_unix.so obscure use_authtok try_first_pass sha512
password        [success=1 user_unknown=ignore default=die]     pam_ldap.so use_authtok try_first_pass
password        requisite                       pam_deny.so
password        required                        pam_permit.so

```

/etc/ldap.conf
```

uri ldaps://ad1-ric.locusdev.net:3269 ldaps://ad2-ric.locusdev.net:3269

base dc=locusdev,dc=net
ldap_version 3

binddn cn=svc binddn,cn=users,dc=locusdev,dc=net
bindpw **REDACTED**

scope sub

pam_login_attribute sAMAccountName
pam_lookup_policy yes

# Modify cn=User,dc=e... to your container with your users.
nss_base_passwd dc=locusdev,dc=net?sub
nss_base_shadow dc=locusdev,dc=net?sub
nss_base_group  ou=groups,dc=locusdev,dc=net?sub

nss_map_objectclass posixAccount User
nss_map_objectclass shadowAccount User
nss_map_objectclass posixGroup Group
nss_map_attribute uid sAMAccountName
nss_map_attribute uniqueMember member
nss_map_attribute userPassword password
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute gecos name
nss_map_attribute cn sAMAccountName

```

---

### Post by martycombs on 2018-12-08
Well Murphy's (or Sod's) Law applied.  As soon as I had posted this when I noticed **libnss-db** was not installed.  After installation, everything worked.

It makes me think though that some error message in debug mode should have indicated the missing dependency.

---

