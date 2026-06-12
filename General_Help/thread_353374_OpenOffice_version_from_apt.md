---
title: "OpenOffice version from apt"
date: 2007-02-04
forum: General Help
---

### Post by PgR on 2007-02-04
HI - hope this is in the right fourm; if not could some kind Mod move it?

I'm running 6.10 on two machines. One's a laptop running kernel 2.6.17-10-386; the other is a desktop running kernel 6.2.17-10-generic. The desktop has an AMD64 proc, but it's running 32-bit Ubuntu 'cos i  couldn't get various apps running in 64-bit. Both machines have universe and multiverse added to their sources.list

Anyway, I installed openoffice with apt on both machines. Apt-get update/upgrade has given the laptop OO version 2.1 - but the desktop is still on version 2.0.4.

As both machines are running the same 32-bit version of Ubuntu, and have the same sources.list, I guess it must be the subtle difference in kernel versions which is preventing the upgrade on the dekstop...


I know I could install the new version from OO.org, but I'm as interested in why this is happening as I am in getting the current version of a particular app running.

Any bright ideas?

---

### Post by Ramses de Norre on 2007-02-04
Are you sure you haven't installed an unofficial deb on the laptop?? The most recent version in the official edgy repos is 2.0.4-0ubuntu4.

```
$apt-cache policy openoffice.org
openoffice.org:
  Installed: 2.0.4-0ubuntu4
  Candidate: 2.0.4-0ubuntu4
  Version table:
 *** 2.0.4-0ubuntu4 0
        500 http://archive.ubuntu.com edgy-updates/main Packages
        100 /var/lib/dpkg/status
     2.0.4-0ubuntu2 0
        500 http://archive.ubuntu.com edgy/main Packages

```

---

### Post by PgR on 2007-02-04
Well Ramses I would swear I hadn't - but apt-cache shows the same result for me (thans for that one) and I've found the installation file for 2.1 in my downloads directory. That must be it.

Thanks for that - I've been trying to figure it out for some time. At least I now know it's my fault. That's something of a relief.

---

