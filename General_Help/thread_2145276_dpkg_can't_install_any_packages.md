---
title: "dpkg can't install any packages"
date: 2013-05-14
forum: General Help
---

### Post by izman on 2013-05-14
I was trying to install some 32 bit libraries on my 64 bit Ubuntu 12.04, and I ended up messing some packages up.

While I fixed a few, for some reason the acpid package refuses to uninstall, regardless what I do.

For any package I try to install via sudo apt-get install, I get the following error:

```
Setting up acpid (1:2.0.10-1ubuntu3) ...
invoke-rc.d: unknown initscript, /etc/init.d/acpid not found.
dpkg: error processing acpid (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo apt-get purge acpid
reports the same error.

I did a quick check in /etc/init.d/ and acpid does not exist.  Is there any way I can manually remove acpid?  I can't even reinstall acpid, because I get the same error above.

Any help?

---

