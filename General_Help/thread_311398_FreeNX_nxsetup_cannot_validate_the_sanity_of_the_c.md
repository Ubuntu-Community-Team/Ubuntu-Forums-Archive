---
title: "FreeNX: nxsetup cannot validate the sanity of the current installation"
date: 2006-12-02
forum: General Help
---

### Post by snakyjake on 2006-12-02
**Problem:**
Cannot connect to FreeNX remotely.

**Error/Warning Messages During install:**
[INDENT]Error when trying to connect to NX server, error is:
NXSSH running with pid: 6965
ssh: connect to host 127.0.0.1 port 22: Connection refused.
nxsetup cannot validate the sanity of the current installation:  the current system or NX configuration could be broken.

[/INDENT]
Trying to install nomachine's FreeNX on Kubuntu (6.10). I'll try to provide as much information I can about the problem, but I'm not even quite sure where to start my troubleshooting.

I downloaded the .deb packages from nomachine's website.  I installed:  nxclient, nxnode, then nxserver.  

I also uninstalled the packages, then reinstalled.  Rebooting also did not work.

Also tried "ssh status", but received "ssh: connect to host status port 22: Connection refused"

Please help...any ideas?

---

### Post by snakyjake on 2006-12-02
FIX:

I did step 3 from this link and it solved my issue.

[http://ubuntuforums.org/showthread.php?t=204976&highlight=freenx+edgy](http://ubuntuforums.org/showthread.php?t=204976&highlight=freenx+edgy)

---

