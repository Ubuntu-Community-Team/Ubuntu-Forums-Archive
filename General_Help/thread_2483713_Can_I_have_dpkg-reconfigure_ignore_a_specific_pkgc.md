---
title: "Can I have dpkg-reconfigure ignore a specific pkg/config-file?"
date: 2023-02-07
forum: General Help
---

### Post by jbygden on 2023-02-07
Can I have dpkg-reconfigure ignore, and not ask user to keep local modified or install maintainers version of a specific config file or for a specific pkg?

We're configuring our clients with ansible, but when the users run apt upgrade and a pkg is updated which contains any of the config files that we've modified for our environment, the user faces the question whether to keep the local, modified version or install the maintainers version of the file.

It would be nice if we somehow could configure [dpkg|apt] to not ask about these files and always choose to keep the local, modified version. 

Is this possible? How?

---

### Post by jbygden on 2023-02-07
Seems like Raphaël Hertzog had the answer in a comment on [https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/:](https://raphaelhertzog.com/2010/09/21/debian-conffile-configuration-file-managed-by-dpkg/:)

> Unfortunately no. In most cases, dpkg is configured to install unmodified configuration files and those that were already modified are managed by an external tool like puppet or cfengine anyway.


---

### Post by ActionParsnip on 2023-02-07
Have a playbook that runs the updates then puts the config files back in that get changed. You can then use the playbook to update client systems using the script and manage it that way

---

