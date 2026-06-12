---
title: "Are there any guides for helping to troubleshoot an ubuntu (or general .deb) package?"
date: 2023-01-30
forum: General Help
---

### Post by Surfrock66 on 2023-01-30
I've got an older ubuntu server running too many services, including openLDAP and kerberos.  I'm splitting this off into a new server, but I'm having trouble with a package installing.  krb5-kdc fails to configure, with the following error 

```
Setting up krb5-kdc (1.19.2-2ubuntu0.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/krb5-kdc.service &#8594; /lib/systemd/system/krb5-kdc.service.
Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 142.
```

I've tested this on an ubuntu server 22.04.1 and 22.10 minimal install, no other packages except all updates from the fresh install.  I have filed a bug about this here, but it's still pending: [https://bugs.launchpad.net/ubuntu/+source/init-system-helpers/+bug/2003756](https://bugs.launchpad.net/ubuntu/+source/init-system-helpers/+bug/2003756) While all other packages seem to install fine, krb5-kdc doesn't, and they think it's an issue with init-system-helpers.  I'm not sure where to look.

In general, is there something I can do to debug a deb package?  I've done "apt-get --download-only install krb5-kdc" and from that done "dpkg -e krb5-kdc_1.19.2-2ubuntu0.1_amd64.deb" where I looked into postinst and the line numbers don't line up (it's only 94 lines long).  I've googled a bit, but can't find any real comprehensive guide for helping to debug a debian package.  Can anyone advise me on what I can do to help debug?

---

### Post by Holger_Gehrke on 2023-01-30
Read carefully: The error isn't in the postinst script itself, it's in the perl-script /usr/bin/deb-systemd-invoke which is 156 lines long and line 142 is
```

system('systemctl', '--quiet', @instance_args, $action, @start_units) == 0 or die("Could not execute systemctl: $!");

```
So systemctl returned some kind of error ...

Holger

---

