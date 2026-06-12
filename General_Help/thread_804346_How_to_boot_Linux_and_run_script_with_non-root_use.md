---
title: "How to boot Linux and run script with non-root user?"
date: 2008-05-23
forum: General Help
---

### Post by abcuser on 2008-05-23
Hi,
in Ubuntu 8.04 Desktop I would like on bootup process to start a script which lauaches one server. But this script should be run with user that is not root, because root doesn't have rights to start the server and I don't want to give root the privilege to start this server.

How to bootup a Linux and run a script with non-root user?
Thanks,
Abcuser

---

### Post by justleen on 2008-05-23
boot scripts are run as root.
To have a script start as a normal user, you can use "su"

as root: ```

su - user -c whoami 
```
this will output "user".. 
su will "pretend" your a different user. the -c option runs a command as that user. (whoami in this case, but change that to what you need)
so you can kick off any script as root running under a different user

---

