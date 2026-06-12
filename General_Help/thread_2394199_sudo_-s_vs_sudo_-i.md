---
title: "sudo -s vs sudo -i"
date: 2018-06-13
forum: General Help
---

### Post by COKEDUDE on 2018-06-13
What is the difference between sudo -s and sudo -i? I tried to read the man pages but do not understand. They both give you a root shell.

---

### Post by TheFu on 2018-06-14
-s retains the current environment for the current userid.  It is like 'su'
-i forces a new shell using the new userid and the enviroment for that userid.  It is like 'su -'

Main differences will be HOME and PATH.
HOME will be either /home/userid or /root/
PATH will be longer with the userid or fairly short, but include /sbin/ for root.

You can just look at the 'env' under each different sudo run to see the differences.

---

### Post by Impavidus on 2018-06-14
Let me try to explain the man pages.```
     -i, --login
                 Run the shell specified by the target user's password data&#8208;
                 base entry as a login shell.  This means that login-specific
                 resource files such as .profile or .login will be read by the
                 shell.  If a command is specified, it is passed to the shell
                 for execution via the shell's -c option.  If no command is
                 specified, an interactive shell is executed.  sudo attempts
                 to change to that user's home directory before running the
                 shell.  The command is run with an environment similar to the
                 one a user would receive at log in.  The Command environment
                 section in the sudoers(5) manual documents how the -i option
                 affects the environment in which a command is run when the
                 sudoers policy is in use.
```
```

     -s, --shell
                 Run the shell specified by the SHELL environment variable if
                 it is set or the shell specified by the invoking user's pass&#8208;
                 word database entry.  If a command is specified, it is passed
                 to the shell for execution via the shell's -c option.  If no
                 command is specified, an interactive shell is executed.
```
Both will run a shell as the root user (or some other user, sudo doesn't just do root). The difference is that sudo -s will use the shell and environment of the user calling sudo. It will not move you to a different directory and $HOME points still to your own home directory. If your shell is bash but root's shell is dash, it will still run bash.

On the other hand, sudo -i will use the shell and environment of the user you are switching to. It will change directory to /root (or the home directory of whatever user you're switching to) and will change $HOME accordingly. If your shell is bash but root's shell is dash, it will run dash.

---

