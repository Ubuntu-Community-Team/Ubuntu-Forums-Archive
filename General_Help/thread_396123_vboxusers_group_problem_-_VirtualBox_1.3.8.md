---
title: "vboxusers group problem - VirtualBox 1.3.8"
date: 2007-03-29
forum: General Help
---

### Post by jfinkels on 2007-03-29
VirtualBox 1.3.8, Ubuntu 6.10, Intel x86

I installed VBox 1.3.8 from the Virtual Box website ([http://www.virtualbox.org/](http://www.virtualbox.org/) - they have a nifty edgy deb), and I added myself to the group *vboxusers* as is 'required' to run virtual machines. However, when I run the command "VirtualBox", I get the following message:

```

jeff@jeff-laptop:~$ VirtualBox 
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.

```

Does anyone know of a fix to this problem, or has anyone else run into this problem?

---

### Post by jfinkels on 2007-03-29
Figured out how to edit /etc/group manually: I am in the vboxusers group, I think...
```

vboxusers:x:1001:root,jeff

```

---

### Post by ikki_72 on 2008-04-23
tried the same but still got
> WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.

I did
```
vboxusers:x:1001:root,umarzuki
```

---

### Post by raulih on 2008-04-27
1. Add yourself to vboxusers group:

```
usermod -a -G vboxusers usernamehere
```

2. Logout and re-login. I hope you've done that already ;)

---

