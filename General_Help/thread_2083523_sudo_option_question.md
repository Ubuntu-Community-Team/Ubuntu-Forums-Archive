---
title: "sudo option question"
date: 2012-11-12
forum: General Help
---

### Post by pellyhawk on 2012-11-12
Hi, I wish to transform to root and have a question about sudo -i. I typed "man sduo" and got:
```
       -i [command]
                   The -i (simulate initial login) option runs the shell specified in the
                   passwd(5) entry of the target user [COLOR="Red"]as a login shell.[/COLOR]  This means that
                   login-specific resource files such as .profile or .login will be read by
                   the shell.  If a command is specified, it is passed to the shell for
                   execution.  Otherwise, an interactive shell is executed.  sudo attempts to
                   change to that user's home directory before running the shell.  It also
                   initializes the environment, leaving DISPLAY and TERM unchanged, setting
                   HOME, SHELL, USER, LOGNAME, and PATH, as well as the contents of
                   /etc/environment on Linux and AIX systems.  All other environment variables
                   are removed.

```

I noticed many people said "sudo -i" can transform to root. But I did not find out anything about "root" in the help info I posted above, only found that"as a login shell.". Where can I find it out? Thanks.

---

### Post by wojox on 2012-11-12
[RootSudo]("https://help.ubuntu.com/community/RootSudo#root_account")
> Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent Root login, the best alternative is to simulate a Root login shell using the following command...
```
sudo -i
```

---

