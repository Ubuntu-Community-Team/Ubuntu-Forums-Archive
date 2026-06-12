---
title: "Login PAM slowness using SSSD + AD"
date: 2021-11-04
forum: General Help
---

### Post by loopix on 2021-11-04
Hey, 


**_I'm having a slowness problem on our Ubuntu Server :_**
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal

```


**_First, let me describe the problem : _**
- at login (SSH, or even locally using su)
- user is authenticated and authorized
- then there is a group lookup (this is my issue)
- then user is finally dropped at its shell
=> first access (no cache on SSSD) = 3 to 10s+
=> next try (with cache) = 1s


**_We are also running RHEL 7/8 servers with about same settings : _**
- at login (SSH, or even locally using su), there is NO slowness
- user is authenticated and authorized
- then there is NO group lookup (and so, no slowness issue)
- then user is finally dropped at its shell
=> first access (no cache on SSSD) = 1s
=> next try = still 1s (in fact it's even less)


I already spent hours to try to find where the groups are being loaded at login.
I'm suspecting that PAM is doing that on Ubuntu but not on RHEL.


[B][U]Here are my findings : 
[/U][/B]- not related to local user (root or a simple local test user works just fine)
- totally related to AD users (only AD users are impacted due to their groups)
- not from home folder (empty)
- not from bash* / profile* / login* wide setting under /etc/
- not from ssh (same with su)
- not from su <username> or su - <username> (login shell)
- not from sssd (about same as the one used on RHEL 7/8)
- not from motd (dynamic)
- not from nsswitch.conf
- not from PAM ?!? (unconfirmed)
- not from systemd ?!? (unconfirmed)

- it's NOT related to SSH as it also happen just by using "su" 
- at login, I can see that "id <username>" is super fast where it should not (it means that at login, it loaded groups to cache)
- on RHEL 7/8, login is fast because groups are not loaded and so, using "id <username>" after login will take some seconds (as not loaded and so, that's why it's fast at login but not at "id")
- my guess is that it's all related to PAM settings only
- did some debug (SSHd) but was not able to debug PAM (yet)


[B][U]Some technical information :
[/U][/B]- SSHd (using password) : 
```
debug1: attempt 3 failures 2 [preauth]
debug3: PAM: sshpam_passwd_conv called with 1 messages
SLOW_at_that_point
debug1: PAM: password authentication accepted for <hidden>

```

- Syslog (using password) : 
```
Nov  4 11:40:38 vu2400005 sshd[49692]: pam_sss(sshd:auth): authentication success; logname= uid=0 euid=0 tty=ssh ruser= rhost=<hidden> user=<hidden>
SLOW_at_that_point
Nov  4 11:40:52 vu2400005 sshd[49692]: Accepted password for <hidden> from <hidden> port 51168 ssh2

```
=> issue the ssh command on client
=> type password
=> then wait ... then ok


**_My only question :_** where and how can I update this behavior (avoid loading user's groups at login time) ?


**_Please note : _**
- not a DNS issue
- not a SSSd issue (it works just fine and as expected and with Kerberos ticketing also)
- not a SSHd issue (can be reproduced without using SSHd)
- about same behavior as on RHEL 7/8 (BUT is loading groups where I'm not expecting that and so, login time is longer)


If someone has any good idea, go for it :)


Thanks

---

