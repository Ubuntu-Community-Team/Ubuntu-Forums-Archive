---
title: "Quota Problem"
date: 2006-10-31
forum: General Help
---

### Post by DannyG on 2006-10-31
I have installed quota on my system by carrying out the following steps:

```
apt-get install quota
```

```
vi /etc/fstab
```

and added

```
usrquota,grpquota
```

```
touch /quota.user /quota.group
chmod 600 /quota.*
mount -o remount /
quotacheck -avugm
```

But, when I do:

```
quotaon -avug
```

I get:

```
quotaon: using //quota.group on /dev/sda1 [/]: No such process
quotaon: Quota format not supported in kernel.
quotaon: using //quota.user on /dev/sda1 [/]: No such process
quotaon: Quota format not supported in kernel.
```

I am using Ubuntu Dapper.

Any ideas on this please?

Thanks,

Daniel.

---

### Post by matthewstory on 2006-10-31
looks like you need to go plug in the quota kernel modules by hand.  Don't know exactly what they are but there is a nifty curses tool for the CLI that makes this very easy:

sudo aptitude install modconf

Then you just run modconf with no options, and browse to the quota kernel modules, and plug them in.

---

