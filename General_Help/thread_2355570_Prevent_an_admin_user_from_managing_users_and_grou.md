---
title: "Prevent an admin user from managing users and groups"
date: 2017-03-14
forum: General Help
---

### Post by Mamoth on 2017-03-14
Hello.

On my system (Xubuntu 16.04 but I don't believe it matters in this case), there is a user which needs to have admin rights (*sudo *capability) but that I want to prevent fro mbeing able to manage user accounts and groups (i.e. : he must not be able to add/delete/edit user accounts or groups).

Is this possible and then how ?

---

### Post by TheFu on 2017-03-14
Look into the **sudoers** file (manpage [https://www.sudo.ws/man/1.8.15/sudoers.man.html](https://www.sudo.ws/man/1.8.15/sudoers.man.html) is excellent). You can specify exactly which commands a user or group can run through sudo with settings inside the sudoers.  Just be certain that you don't allow editing anything via sudo, since most editors will allow shelling out and that would provide a full root shell.  Also, don't let them 'mount' - mount is extremely powerful.

So - start by making a list of exact things, with exact options (if you care to that level), to be required for the user.
Some more ideas: [http://www.unix.com/unix-for-advanced-and-expert-users/178578-sudo-blocking-specific-commands.html](http://www.unix.com/unix-for-advanced-and-expert-users/178578-sudo-blocking-specific-commands.html)

---

