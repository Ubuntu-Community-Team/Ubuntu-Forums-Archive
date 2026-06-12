---
title: "Most snaps denied by apparmor"
date: 2021-03-24
forum: General Help
---

### Post by alchemistjosh on 2021-03-24
Hello everyone,

I'm having a problem in which **apparmor denies most snaps from running**. This issue started for me yesterday after a handful of updates were installed via Software Updater. Snaps had been running without problems beforehand, and I did not make any  intentional system or configuration changes. I'm on Ubuntu 20.04 with snap v.2.49.1 as below:
```

josh@dwarven-notebook:~$ snap version
snap    2.49.1
snapd   2.49.1
series  16
ubuntu  20.04
kernel  5.9.8-050908-generic

```

The "hello-world" snap executes without problems, but anything else I have installed (LibreOffice, Bitwarden, Only Office, and more) fail similarly. Attempting to run LibreOffice, for example, gives a [string of permissions errors shown here]("https://paste.ubuntu.com/p/dds6FfK8Rb/").

Attempting to run the suggested command also fails:
```

josh@dwarven-notebook:~$ gdk-pixbuf-query-loaders > /home/josh/snap/libreoffice/common/.cache/gdk-pixbuf-loaders.cache
gdk-pixbuf-query-loaders: command not found

```

The [official snap troubleshooting guide]("https://snapcraft.io/docs/debug-snaps") suggests examining the output of journalctl, which [indicates apparmor is behind the denial as shown here]("https://paste.ubuntu.com/p/s4s9Gj9PFs/"). I'm unfortunately not sure how to use this information.

A few forum posts have indicated that non-standard home directory paths aren't tolerated well. My home directory is on a separate partition from root, but it is still mounted as /home, so I don't think that's a part of the problem.

In the hopes that it would be an easy fix, I fully removed snapd and apparmor with [FONT=courier new]apt purge snapd[/FONT] and [FONT=courier new]apt purge apparmor[/FONT], then reinstalled them & LibreOffice. No change there; I receive the same error messages. **This issue is not limited to LibreOffice**; I get the same results with any of the snaps I've tried executing (with the exception of "hello-world").

I would really appreciate any help you can offer.

---

### Post by TheFu on 2021-03-24
Don't use a snap for libreoffice? Use either the normal package or a trusted PPA with the newer version needed.
The same can be said for most other snaps.  The only snap that I don't think is available in any other way is the lxd snap.  Which is really too bad.

> A few forum posts have indicated that non-standard home directory paths aren't tolerated well. My home directory is on a separate partition from root, but it is still mounted as /home, so I don't think that's a part of the problem.

That's an understatement.  If the home isn't in /home/ and mounted locally, it will not work.  

NFS storage mounted to /home doesn't work with snaps either.  The snap team is blaming the NFS team.  If the **getent passwd** command says where the user's home directory is located, the snaps should work with it - PERIOD. No excuses. Anything less is broken.

---

### Post by alchemistjosh on 2021-03-25
Thank you for taking the time to reply. However, I'm hoping to resolve this problem rather than circumvent it.

---

