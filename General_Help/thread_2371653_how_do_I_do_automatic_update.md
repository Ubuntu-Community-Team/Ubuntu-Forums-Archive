---
title: "how do I do automatic update?"
date: 2017-09-17
forum: General Help
---

### Post by Old Jimma on 2017-09-17
Hi Forum People!

I want to do automatic updates and found advice at [https://help.ubuntu.com/lts/serverguide/automatic-updates.html]("https://help.ubuntu.com/lts/serverguide/automatic-updates.html")

As I understand it, the idea is to edit /etc/apt/apt.conf.d/50unattended-upgrades and adjust the following to "fit my needs needs. according to the documentation

> 
Unattended-Upgrade::Allowed-Origins {
        "${[COLOR="#FF0000"]distro_id[/COLOR]}:${[COLOR="#FF0000"]distro_codename[/COLOR]}";
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};


Really?

> 
Unattended-Upgrade::Allowed-Origins {
        "${[COLOR="#FF0000"]distro_id[/COLOR]}:${[COLOR="#FF0000"]distro_codename[/COLOR]}";
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};


I wondered what the distro_id and distro codename of my machine was and did a

> cat /etc/lsb-release

and got:

> 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"


Really!

Does this mean the appropriate modification to the Unattended Upgrade code listed above is:

> 
Unattended-Upgrade::Allowed-Origins {
        "${[COLOR="#FF0000"]Ubuntu[/COLOR]}:${[COLOR="#FF0000"]16.04[/COLOR]}";
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};


Thanks!
Old JImma from the Old County

---

### Post by untrustytahr on 2017-09-17
No.

It just means you uncomment the lines for the update type you want (i.e. security update, backport, etc).

You uncomment a line by removing the double slashed "//" at the beginning of the line.

Those things you changed are variables that the shell will expand when it's run.

---

### Post by pauljw on 2017-09-17
One other thing, I recommend not uncommenting "proposed" as it will lead to problems.

---

### Post by Old Jimma on 2017-09-17
Hi All:

Is it really true that as untrustytar says, "...Those things you changed are variables that the shell will expand when it's run?"

IF that's the case, when I use synaptic, why isn't my computer up to date? THere are always  a bunch of packages that need updating?

Thanks,
Old JImma

---

### Post by deadflowr on 2017-09-17
> **Old Jimma said:**
> Hi All:

Is it really true that as untrustytar says, "...Those things you changed are variables that the shell will expand when it's run?"

IF that's the case, when I use synaptic, why isn't my computer up to date? THere are always  a bunch of packages that need updating?

Thanks,
Old JImma

automatic updating only runs once a day.
So anything that comes in after that won't be a part of the auto updates.

And to top that off you only have security updates set to auto update.
If you set -updates to also update, more packages will get updated.

(whereas most, if not all, -security updates are also -update packages.
Not all -updates packages are also -security packages)

Hope it make sense.

---

### Post by untrustytahr on 2017-09-17
If you want to know if/when unattended upgrades ran, you can look in the log:

```
tail /var/log/unattended-upgrades/unattended-upgrades.log
```

---

