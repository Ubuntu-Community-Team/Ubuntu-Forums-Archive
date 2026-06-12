---
title: "become temporary root?"
date: 2024-05-18
forum: General Help
---

### Post by billywyatt2 on 2024-05-18
i am running Ubuntu 24.04 and have tried to open Synaptic package manager and failed at each and every attempt because it requires an administrator password which i don't have. Could someone help me please. I only want to become "root" on a temporary basis and not permanently. How could i be added to the sudoers list?

---

### Post by dragonfly41 on 2024-05-18
If in terminal you run command:

man sudo

you can read the option

sudo -H

     -H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.


Thus run ..

sudo -H synaptic

---

### Post by Dennis N on 2024-05-18
> it requires an administrator password which i don't have
If you are in the sudo group, it's just your user password that's needed - the same one you use to login to your user session.  
If you are the only user of the computer, you should already be in that group.
You can also check with 'groups' command in the terminal. Is 'sudo' among the output results?

---

### Post by MAFoElffen on 2024-05-18
+1 ---

If your password does not work to enable Synaptic to do anything, then you are not in the sudoers file, and you do not have the rights and privileges to elevate permissions to install system wide packages... Yes.

That is how things are designed to work.
```

groups | grep 'sudo'

```
Does that show you are in the sudo group?

---

