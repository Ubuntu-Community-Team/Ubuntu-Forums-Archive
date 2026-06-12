---
title: "dpkg says Im not a superuser!"
date: 2007-06-23
forum: General Help
---

### Post by jonandel on 2007-06-23
Hi,

I was running the Software Installer when the PC died.
Now I can't run the update manager as it says 'Index is broken.'  Helpfully, the error then goes on to say 'It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.'

When I run the command in a terminal window, I get another error.. 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. '

When I run the dpk command - I get the final error 'dpkg: requested operation requires superuser privilege'

Problem is my account is an Administrator - with all privs selected.

Now what !?

---

### Post by ronocdh on 2007-06-23
> **jonandel said:**
> Hi,

I was running the Software Installer when the PC died.
Now I can't run the update manager as it says 'Index is broken.'  Helpfully, the error then goes on to say 'It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.'

When I run the command in a terminal window, I get another error.. 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. '

When I run the dpk command - I get the final error 'dpkg: requested operation requires superuser privilege'

Problem is my account is an Administrator - with all privs selected.

Now what !?
Precede the command with **sudo**, i.e.:
```
sudo dpkg --configure -a
```

---

