---
title: "Enable network in recovery mode in 17.10?"
date: 2017-11-27
forum: General Help
---

### Post by again? on 2017-11-27
in 17.04 I can boot in recovery mode, drop to to root shell, remount the file system read/write and enable networking.
eg
```
mount -o rw,remount /
dhclient enp3s0
```

In 17.10 using same procedure, "apt update" fails to resolve.

An already broken recovery mode is now more useless. ](*,)
Anyone know how to enable networking?

---

### Post by SeijiSensei on 2017-11-28
So the problem is a broken resolver?  Or is it really the lack of a network connection?  Can you run "ping 8.8.8.8" and get replies?  If so, the brute-force solution during recovery is to overwrite /etc/resolv.conf so it points to valid nameservers like this:
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
Any better?

---

### Post by again? on 2017-11-29
This worked.
/etc/resolv.conf already existed but was a link to a file in /run/systemd/resolve/ and I could not write to it.
I had to delete the link then recreate /etc/resolv.conf  with the google dns servers.

May not be a problem with recovery mode specifically but more with systemd and dns resolving in 17.10.
Thanks.

---

