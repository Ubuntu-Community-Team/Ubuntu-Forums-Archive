---
title: "Issue with sftp through Nautlius."
date: 2014-07-15
forum: General Help
---

### Post by Liam W on 2014-07-15
Hi,

I'm having an annoying issue connecting to an sftp server through Nautlius - normal ftp works fine.

If I try to connect to an sftp server, I get this message in an error dialog:

```
Don't have permission to access the requested location.
```

However, if I'm running Nautlius with root permissions (using gksu nautlius from the terminal) I get this message underneath the server address entry box in the connect to server dialog:

```
This file server type is not recognised.
```

I am using sftp://xfliam@xf-liam.com as the address.

Can anyone help me with this? It's driving me crazy...

Thanks,
Liam

---

### Post by TheFu on 2014-07-15
Do sftp work correctly from the shell?  If not, check the owner/permissions on ~/.ssh/ files.

If it is just nautilus, check the permissions on the nautilus settings file(s) somewhere under ~/.config/ . Running some GUI program as root (sudo) may have root screw with ownership and permissions of the setting files - this breaks the program for normal user accounts.

---

### Post by Liam W on 2014-07-15
> **TheFu said:**
> Do sftp work correctly from the shell?  If not, check the owner/permissions on ~/.ssh/ files.

If it is just nautilus, check the permissions on the nautilus settings file(s) somewhere under ~/.config/ . Running some GUI program as root (sudo) may have root screw with ownership and permissions of the setting files - this breaks the program for normal user accounts.

I just did some more testing, due to what I discovered when I tried it from the terminal.

Turns out the IP I was connecting to had port 22 closed. Nautilus was throwing the connection refused error like in my OP. I changed the domain to the right one with SSH open, connected perfectly (after adding the key to the key pool using the ssh-add command).

Thanks for the shell suggestion :)

Liam

---

