---
title: "Need help updating ubuntu"
date: 2006-11-01
forum: General Help
---

### Post by boast on 2006-11-01
I was trying to install tk8.5 but it needed a newer version of libfreetype6, which needed a newer libc6, and now I have issues.

```
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu12 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu12 is install ed
  libfreetype6-dev: Depends: libfreetype6 (= 2.1.10-1ubuntu2.2) but 2.2.1-5 is i nstalled

```

Does ubuntu not like to update itself? I don't want to update the whole system manually, that'd take years.

---

### Post by skierkegaard on 2006-11-01
It looks to me like you have newer versions than required.

---

### Post by kelvinchufei on 2006-12-08
1.sudo aptitude update
2.sudo aptitude install build-essential
then it will ask you:

Downgrade the following packages:
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20 (dapper)]

Score is -40

Accept this solution? [Y/n/q/?] y

3.then it will be ok

enjoy!

---

