---
title: "Which best practice for using gedit as root?"
date: 2018-02-25
forum: General Help
---

### Post by amauryat on 2018-02-25
gksudo seeming to be somehow depreciated since 2017 as I see on the [french forum documentation]("https://doc.ubuntu-fr.org/gedit#edition_avec_privileges"), is there an environment and version agnostic best practice allowing to use gedit as root?

  (excluding vim, nano or tee: the use case being a GUI amendment of sources.list for instance)

  My researchs brought me these proposals, are they equivalent or to be rejected :
  
[LIST]
[*]pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY gedit
[*]gedit admin:///path/to/file
[*]sudo -i gedit
[*]sudo -H gedit
[/LIST]


  Any other ?

---

### Post by wildmanne39 on 2018-02-25
It is best to use```
sudo -H gedit
```

---

### Post by #&amp;thj^% on 2018-02-25
> **wildmanne39 said:**
> It is best to use```
sudo -H gedit
```

+1
I agree with wildmanne39
From man sudo
```

-i, --login
                 Run the shell specified by the target user's password data&#8208;
                 base entry as a login shell.  This means that login-specific
                 resource files such as .profile, .bash_profile or .login will
                 be read by the shell.  If a command is specified, it is
                 passed to the shell for execution via the shell's -c option.
                 If no command is specified, an interactive shell is executed.
                 sudo attempts to change to that user's home directory before
                 running the shell.  [U]The command is run with an environment
                 similar to the one a user would receive at log in.  Note that
                 most shells behave differently when a command is specified as
                 compared to an interactive session;[/U] consult the shell's man&#8208;
                 ual for details.  The Command environment section in the
                 sudoers(5) manual documents how the -i option affects the
                 environment in which a command is run when the sudoers policy
                 is in use.
```

```

-H, --set-home
                 Request that the security policy set the HOME environment
                 variable to the home directory specified by the target user's
                 password database entry.  Depending on the policy, this may
                 be the default behavior.

```

---

### Post by sisco311 on 2018-02-25
In Ubuntu 17.10 (gvfs >=  1.29.4) you should use the gvfs admin backend:
```
gedit admin:///path/to/file
```
[https://ubuntuforums.org/showthread.php?t=2377380](https://ubuntuforums.org/showthread.php?t=2377380)
[https://github.com/brunonova/nautilus-admin/issues/29](https://github.com/brunonova/nautilus-admin/issues/29)

---

### Post by amauryat on 2018-02-25
Thank you for your answers !

On Wayland, is URI calling better than ```
sudo -H gedit
``` using *xhost* ?

---

### Post by sisco311 on 2018-02-25
In theory, the gvfs admin backend  method (which uses polkit) is better and safer, regardless of the UI you use. 

You don't run the whole application as root. Privilege escalation happens only when is strictly necessary.

---

### Post by HermanAB on 2018-02-25
Actually, I think the best practise for using gedit as root, is to use nano!

---

### Post by amauryat on 2018-02-26
I do agree, tee being an alternative ! It's not the use case though ;) (nano and tee can afraid some users)

---

