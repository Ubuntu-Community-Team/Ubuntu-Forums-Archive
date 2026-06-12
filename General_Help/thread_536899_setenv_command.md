---
title: "setenv command"
date: 2007-08-28
forum: General Help
---

### Post by satimis on 2007-08-28
Hi folks,


Ubuntu 7.04 lamp server amd64


Which package provides "setenv" command?

$ which setenv
No printout

$ apt-cache policy csh```

csh:
  Installed: 20060813-1
  Candidate: 20060813-1
  Version table:
 *** 20060813-1 0
        500 http://hk.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```
csh already installed.


TIA


B.R.
satimis

---

### Post by aJayRoo on 2007-08-28
What is the output (if any) when you just type 'setenv' without arguments? I thought setenv was a shell command so it should be provided simply by installing the c-shell. Are you sure you are actually using the csh shell? Try ```
echo $SHELL
``` and see what the output is. If it isn't 'csh' then you can try using the 'chsh' command to change the default shell as in ```
chsh -s /bin/csh
```Hope something here can help you.

EDIT: I'm assuming you wish to use csh as your default shell, but if you wanted to use bash, the equivalent command for creating a shell variable is ```
VAR=the_variable_value
export VAR
``` in case you didn't already know.

---

### Post by pmg on 2007-08-28
I suspect that, even though you have csh installed on the system, you were not running a csh shell at the time you ran the **which setenv** command.  In **csh** both **which** and **setenv** are built-in commands.  aJayRoo described how to change your default shell to csh.  If you don't want to do that but just try some things using it, you can just type **csh** to start one in that one window.

---

