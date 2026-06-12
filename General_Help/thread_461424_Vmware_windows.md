---
title: "Vmware windows"
date: 2007-06-01
forum: General Help
---

### Post by Frankie88 on 2007-06-01
I really have not got a clue when it comes to computers let alone linux and ubuntu.

so here is the problem: my vmware no longer opens when i load it.

I type vmware into the terminal and it says:

"vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl."

I type in that command and it replies:

"Please re-run this program as the super user.

Execution aborted."

I type in "su" and my username and password and then type in the "/usr/bin/vmware-config.pl" command and it still says:

"Please re-run this program as the super user.

Execution aborted."

can any one help!!! please? as far as i am aware i am the SU

---

### Post by raja on 2007-06-01
Use sudo instead of su in Ubuntu.
So try the command again, prefixing with sudo.

```
sudo /usr/bin/vmware-config.pl
```

---

