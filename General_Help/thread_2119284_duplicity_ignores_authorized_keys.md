---
title: "duplicity ignores authorized_keys?"
date: 2013-02-23
forum: General Help
---

### Post by TheFu on 2013-02-23
I'm trying to test duplicity because rdiff-backup is behaving funny (i.e. broken) on 1 of the machines here.

The duplicity command is very similar to what rdiff-backup uses, so this is not a big change.


[LIST=1]
[*]I've setup a special userid just for backups, backups, on the remote server with lots-o-storage.
[*]I've verified that sftp works without prompting for a password from the root account to this other non-root, remote, account.  It works perfectly.
[/LIST]
Now when I try 
```
nice /usr/bin/duplicity  /etc  sftp://backups@remsrv/Backups/lubuntu

```
it prompts for a password.  Huh?  The "backups" account does not have a password - that is by design.

The man page seems to imply that either external programs for ssh/scp/sftp are used or a built-in python implementation.
Also tried adding ```
--ssh-backend pexpect
``` option. No different.

Ideas?  It must be something simple, right?

---

