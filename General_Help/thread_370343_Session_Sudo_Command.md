---
title: "Session Sudo Command"
date: 2007-02-25
forum: General Help
---

### Post by Maxtr0sity on 2007-02-25
As I understand, System->Preference->Sessions->[Startup Programs] is exactly the same as Startup in Windows correct? I have placed a few commands in there but a few needs 'sudo-level' access to run, can I simply put in the same command?

Ex. sudo laptop-mode start

My theory is, since it requries a password prompt, the script will simply not run.

---

### Post by Tichondrius on 2007-02-25
Right.

If you need to run anything as root, you can either add it as a service, or use the "startup programs" with sudo like you said, but change sudoers file to not require a password. This is explained in ubuntuguide.org.

---

