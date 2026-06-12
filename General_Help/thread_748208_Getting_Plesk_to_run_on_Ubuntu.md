---
title: "Getting Plesk to run on Ubuntu"
date: 2008-04-07
forum: General Help
---

### Post by SteveHillier on 2008-04-07
Further to previous posts I have now overcome Plesk installation problems on Gutsy

Other posts have reported, as I did, that there was a problem with the hostname settings.

If you receive this error then you should try editing /etc/hosts.and make sure you have all possible hosts in the loopback line.  it should read something like
hostname, domainname, hostname.domainname localhost localhost.localdomain
my line reads
```
127.0.0.1 webserver localhost webserver.hchosting.org.uk localhost.localdomain hchosting.org.uk
```

This matches the layout in a Fedora setup.

Plesk install then ran without problem

Sorry for previous rants.

---

