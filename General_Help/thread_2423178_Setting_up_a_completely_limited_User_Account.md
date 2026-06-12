---
title: "Setting up a completely limited User Account?"
date: 2019-07-18
forum: General Help
---

### Post by GhX6GZMB on 2019-07-18
Hello All,

I'm running Lubuntu 19.04 and would like to set up a totally >braindead< user account.

I've created a new user "guest" with no group affiliations and a few programs. My target is to let this user only have access to /home/guest plus subdirectories. As it is now, "guest" has read-only access to the rest of my machine, which I do not want. Everything other than /home/guest should be invisible or blocked.

As a new Lubuntu/Linux user, I'm a bit in over my head here. Can anyone suggest a solution or point me in the right direction, please? I've searched and searched, but the hits all point in the opposite direction: how to extend permissions.

Thank You.

---

### Post by TheFu on 2019-07-18
```
NAME
       rbash - restricted bash, see bash(1)

RESTRICTED SHELL
       If bash is started with the name rbash, or the -r option is supplied at
       invocation, the shell becomes restricted.  A restricted shell  is  used
       to  set  up an environment more controlled than the standard shell.  It
       behaves identically to bash with the exception that the  following  are
       disallowed or not performed:
....

```
There are other shells with a restricted option.

You could also setup a chroot environment to be even more restrictive.  These techniques have been around for 30 yrs.  Pick up a used systems admin book from the mid-1990s and there is a guide inside for setting up stuff like this.  There are subtle permissions required to fully lock down users to specific locations. Miss 1 and a smart user will get out.

---

### Post by GhX6GZMB on 2019-07-19
Hmmm... searching further, it seems more likely that jails or containers are the solution to my problem. Does anyone have experience here? I'm looking at LXC.
A very basic question: do I set up the braindead user first, or do I create the container first?

Thanks.

---

