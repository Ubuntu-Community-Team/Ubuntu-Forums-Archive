---
title: "Super User is no more"
date: 2008-03-11
forum: General Help
---

### Post by vortmax on 2008-03-11
I have a machine running feisty server that apparently no longer has a super user.  Not sure how it happened, don't really care, but now I can't really do anything with the machine.  It's still working fine, but I can't update it or admin it or even shut the dang thing down.

So...how can I get into a root console to add a user to the sudoers?  Can you boot straight into a root shell by using 'kernel single' as the boot string?  I've done that a handfull of times in redhat, but that OS also let you log in as root by default.

---

### Post by jken146 on 2008-03-11
Any users in the admin group can use [sudo]("https://wiki.ubuntu.com/RootSudo") to run commands as root.

To boot in single user mode, just select Recovery Mode at the GRUB menu.  This will dump you into a root shell, with no password required.

You don't have to actually edit /etc/sudoers -- just add the user(s) you want to the admin group.

FYI, there *is* a super user, but no password is set for root.  In this way, the account is locked.

---

### Post by taurus on 2008-03-11
Just add your login name to group admin in /etc/group from the recovery mode.

```
nano B /etc/group
```

---

### Post by sisco311 on 2008-03-11
the command is:
```
usermod -a -G admin ***username***
```

---

