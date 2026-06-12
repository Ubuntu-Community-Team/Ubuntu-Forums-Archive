---
title: "PAM SELinux etc et.al."
date: 2005-06-24
forum: General Help
---

### Post by AndEat on 2005-06-24
I have been wading through the material I could find on PAM and was wondering if anyone would be able to suggest some directions for learning.

Most of what is available is straightforward, but where can I find info on how to add authorization to programs....e.g. having firefox require some sort of login. Is this possible? I want to play around with one relatively simple program before I start working on the whole system.

How does PAM work with SELinux? Seems as though SELinux would make PAM obsolete. I haven't done any research yet, so I am just [COLOR=Teal]curious[/COLOR] at this point.

---

### Post by Javier Godinez on 2005-08-25
As far a PAM goes, it requires an selinux module. Take a look at Fedora's /etc/pam.d/login, it requires pam_selinux.so. As far as I know Ubuntu does not support this yet! Hopefully the next release will!

Javier Godinez

---

### Post by raycast on 2007-04-01
PAM and SELinux are complimentary, so no, SELinux does not in any way replace PAM.

PAM is about authentificating users, e.g. by checking their password.

SELinux is about doing access control, and _relies_ on users having their identity already checked.

The PAM module SELinux comes with is to set the appropriate SELinux identity when the user logs in, and eventually offering him the choice of which identity to use.

For example, a user might be able to login with 'user' privileges and with 'staff' privileges. For securitry reasons, he can't run his web browser when logged in as 'staff', but then he can access some log files. So he'll likely login as 'user', and then re-login in a subshell with 'staff' privileges to access the log files.

Note that PAM is kind of low-level. This is intentional. It's essential to the system operation, and you'll definitely want to be able to login as root on a seriously broken system to be able to repair it.
PAM is kind of inconvenient to use in high-level applications such as the web server, but you probably can't satisfy both needs directly.

If you want to restrict users from being able to run e.g. firefox (and this includes being able to download firefox into their $HOME and run it from there), SELinux is the only way to go. But it's far from easy. (note that AppArmor does NOT allow that to be done.)

---

