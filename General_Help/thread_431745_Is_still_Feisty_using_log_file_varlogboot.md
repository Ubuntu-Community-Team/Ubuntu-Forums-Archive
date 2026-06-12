---
title: "Is still Feisty using log file /var/log/boot ?"
date: 2007-05-03
forum: General Help
---

### Post by Psykotik on 2007-05-03
Since I upgraded to Feisty, log file /var/log/boot is no more updated by the boot process.

Can someone confirm ? Is it an expected feisty's behaviour or is it a bug which deserve to be reported ?

Thanks.

---

### Post by Psykotik on 2007-05-04
no one ?

---

### Post by dcstar on 2007-05-05
> **Psykotik said:**
> Since I upgraded to Feisty, log file /var/log/boot is no more updated by the boot process.

Can someone confirm ? Is it an expected feisty's behaviour or is it a bug which deserve to be reported ?

Thanks.

What does /etc/default/bootlogd say?

---

### Post by Psykotik on 2007-05-05
> **dcstar said:**
> What does /etc/default/bootlogd say?

bootlogd was on "No". Well, I thought you have the solution, but.... I turned to "yes", I even tried to let it empty, but no new bootlog is written.

In other words,

```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
```
and
```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=
```
did not change my problem.

---

### Post by Ol'man on 2007-05-07
> **Psykotik said:**
> 
```
BOOTLOGD_ENABLE=Yes
```
I turned to "yes", I even tried to let it empty, but no new bootlog is written.


I have installed a text-only system to a new server and stuck with the same problem (7.04-alternate-i386).

The above variable will only cause any effect when set to "No".
Adding -x to the shebang line of /etc/init.d/bootlogd revealed that the /sbin/bootlogd binary is missing.

No clue if I had been deleting it inadvertently or if it's missed from install. Can anyone tell me what package I will have to re-install to get it back? Searching with aptitude within package repositories did not found any occurence of the string "bootlogd".

Regards

Olaf

---

### Post by Ol'man on 2007-05-08
To give this thread a resume: there is no more bootlogd with Ubuntu. The boot messages are copied from the kernel's ring buffer into */var/log/dmesg* within init process. This is done by */etc/init.d/bootmisc.sh.*

The */etc/init.d/bootlogd* startup script seems to be a residue from former times. Simply have ```
"BOOTLOGD_ENABLE=No"
``` in */etc/default/bootlogd* to get rid of it.

---

### Post by Psykotik on 2007-05-08
Thanks for this answer !

---

### Post by loa on 2007-11-09
This is also reported as a bug in [https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955) and [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120). So apparently they are trying to fix this and get /var/log/boot working in the old way again.

---

