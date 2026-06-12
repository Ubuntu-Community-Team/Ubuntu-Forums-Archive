---
title: "How to upgrade ClamAV engine regularly and automatically?"
date: 2007-07-18
forum: General Help
---

### Post by scotty64 on 2007-07-18
Is there an easy way to keep the ClamAV engine uptodate without manual intervention? Debian has the useful "Volatile" repository that makes this an easy job. Is there anything like this on Ubuntu? If not it would be great if new ClamAV versions would be regularly backported to Dapper.

---

### Post by Koybe on 2007-07-18
I've no answer but I'm interested in that too ;)

---

### Post by MasterXandrex on 2007-07-26
As Am I

---

### Post by dpar on 2007-07-26
re you talking about signatures?? [http://www.clamav.net/doc/latest/html/node20.html](http://www.clamav.net/doc/latest/html/node20.html)

---

### Post by fmuhandi on 2008-06-12
> **UbuntuUser3859 said:**
> As Am I

Try this one ;

echo deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free >> /etc/apt/source.list

and then apt-get update
after that apt-get upgrade clamav

and if you having problem sample :

The following packages have been kept back:
  clamav clamav-freshclam libclamav3
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

then do this command :
aptitude full-upgrade

It will automatically upgrade your clamav library.

Done.. now your clamav is already using the latest update :).
test your clamav with this command :

clamscan --version

I hope that help.
Cheers,
Fmuhandi

---

