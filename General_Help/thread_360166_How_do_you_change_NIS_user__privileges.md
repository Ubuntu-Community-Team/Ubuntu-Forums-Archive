---
title: "How do you change NIS user  privileges?"
date: 2007-02-12
forum: General Help
---

### Post by BrianK on 2007-02-12
My NIS server is an Ubuntu machine running Ubuntu 6.06.

My new client machine is running Ubuntu 6.10.

With my old client machine (running Ubuntu 5.10), just setting the privileges on the server was good enough - somehow they cascaded down to the client. With the new machine, however, that doesn't happen.

For instance, "Synaptic" is not in the administration menu on the new machine when I'm logged in as me, but it was on the old machine.  It is on the new machine if I log in as one of the local users.

In the past, I've added
[FONT="Courier New"]auth optional pam_group.so[/FONT]
to /etc/pam.d/common-account

and
[FONT="Courier New"]"*;*;*;Al0000-2400; audio,floppy,video,cdrom,plugdev"[/FONT]
to /etc/security/group.conf

but, still no admin abilities when logged in as an NIS person with admin abilities.

ideas?

---

