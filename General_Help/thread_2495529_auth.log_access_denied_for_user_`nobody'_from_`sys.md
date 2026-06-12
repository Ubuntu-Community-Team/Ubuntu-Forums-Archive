---
title: "auth.log: access denied for user `nobody' from `systemd-user'"
date: 2024-02-22
forum: General Help
---

### Post by 0x19xx on 2024-02-22
Hello all,

I've been seeing a lot of the following in my xenial auth.log: ```

systemd: pam_succeed_if(systemd-user:account): 'uid' resolves to '65534'
systemd: pam_succeed_if(systemd-user:account): requirement "uid < 2000" not met by user "nobody"
systemd: pam_access(systemd-user:account): access denied for user `nobody' from `systemd-user'
runuser: pam_unix(runuser-l:session): session opened for user nobody by (uid=0)
runuser: pam_unix(runuser-l:session): session closed for user nobody

``` 
The action being taken is in accordance with /etc/pam.d/common-account:
```

account    [success=1 new_authtok_reqd=done default=ignore]      pam_unix.so
account    requisite            pam_deny.so
account    required            pam_permit.so
account    sufficient                      pam_succeed_if.so uid < 2000
account    required                        pam_access.so
account    [success=ok new_authtok_reqd=done ignore=ignore user_unknown=ignore authinfo_unavail=ignore default=bad]        pam_ldap.so minimum_uid=2000

```
but I cannot figure out what exactly is trying to run as user nobody.
I found the following in syslog:
```

systemd[1]: Created slice User Slice of nobody.
systemd[1]: Starting User Manager for UID 65534...
systemd[1]: Started Session c7289 of user nobody.
collectd[15403]: 0 Success: 1 value has been dispatched.
collectd[15403]: message repeated 21 times: [ 0 Success: 1 value has been dispatched.]
systemd[32704]: user@65534.service: Failed at step PAM spawning /lib/systemd/systemd: Operation not permitted
systemd[1]: Started User Manager for UID 65534.
systemd[1]: Stopped User Manager for UID 65534.
systemd[1]: Removed slice User Slice of nobody.

```
and when I check that [EMAIL="user@65534.servic"]user@65534.servic[/EMAIL]e, it indeed seems it cannot be started:
```

&#9679; user@65534.service - User Manager for UID 65534
   Loaded: loaded (/lib/systemd/system/user@.service; static; vendor preset: enabled)
   Active: inactive (dead)


systemd[31364]: pam_succeed_if(systemd-user:account): requirement "uid < 2000" not met by user "nobody"
systemd[31364]: pam_access(systemd-user:account): access denied for user `nobody' from `systemd-user'
systemd[1]: Started User Manager for UID 65534.
systemd[1]: Stopped User Manager for UID 65534.
systemd[1]: Starting User Manager for UID 65534...
systemd[32704]: pam_succeed_if(systemd-user:account): 'uid' resolves to '65534'
systemd[32704]: pam_succeed_if(systemd-user:account): requirement "uid < 2000" not met by user "nobody"
systemd[32704]: pam_access(systemd-user:account): access denied for user `nobody' from `systemd-user'
systemd[1]: Started User Manager for UID 65534.
systemd[1]: Stopped User Manager for UID 65534.

```
but I cannot figure out exactly what needs this or why it needs to be started every once in a while or by what.

I did a grep for "nobody" and "65534" in /usr/lib/systemd/ and /etc/systemd but came up short. Likewise, I checked /etc/cron but apart from /etc/cron.daily/popularity-contest, which I removed in the meantime, there's nothing that runs as user nobody.

For the life in my I cannot figure out what tries to start this service or for what purpose. I also can't disable the "user@65534.service" because it's static and I'm also not sure it's a good idea.

Btw, the user itself:
```

# getent passwd nobody
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin

```

Please help.

---

### Post by yancek on 2024-02-22
The links below should provide some useful information.

[https://wiki.ubuntu.com/nobody](https://wiki.ubuntu.com/nobody)

[https://en.wikipedia.org/wiki/Nobody_(username)](https://en.wikipedia.org/wiki/Nobody_(username))

---

### Post by 0x19xx on 2024-02-23
> **yancek said:**
> The links below should provide some useful information.
Yeah, it doesn't. I don't have NFS running :)

---

### Post by yancek on 2024-02-23
Don't have any further suggestions.  You might try updating to a supported system since support for xenial ended nearly 3 years ago.

---

