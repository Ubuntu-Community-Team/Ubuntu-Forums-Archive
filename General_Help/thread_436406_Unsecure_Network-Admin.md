---
title: "Unsecure Network-Admin"
date: 2007-05-07
forum: General Help
---

### Post by Shadow503 on 2007-05-07
I would like my guest user to be able to use this feature, but I do not want to give him root/admin access. Any ideas?

---

### Post by Jeremy23 on 2007-05-07
I haven't tested the following code, but if you run this in the terminal:

```
EDITOR=gedit sudo visudo
```

and paste the following at the bottom of the file:

```
Cmnd_Alias      GUEST_CMDS = /usr/bin/network-admin

guest           ALL=(ALL) GUEST_CMDS
```

it should work. Obviously, replace "guest" with the name of the user.

---

### Post by IcemanV9 on 2007-05-07
OR .. open the Users and Groups tool from System --> Administration menu. Then click on the user and then on properties. Choose the User Privileges tab. In the tab, find Executing system administration tasks and check that.

---

### Post by Jeremy23 on 2007-05-07
> **IcemanV9 said:**
> OR .. open the Users and Groups tool from System --> Administration menu. Then click on the user and then on properties. Choose the User Privileges tab. In the tab, find Executing system administration tasks and check that.
But he said he didn't want to give him root/admin access.

---

### Post by Shadow503 on 2007-05-12
> **Jeremy23 said:**
> I haven't tested the following code, but if you run this in the terminal:

```
EDITOR=gedit sudo visudo
```

and paste the following at the bottom of the file:

```
Cmnd_Alias      GUEST_CMDS = /usr/bin/network-admin

guest           ALL=(ALL) GUEST_CMDS
```

it should work. Obviously, replace "guest" with the name of the user.

Thanks for the help, but it doesn't work quite right. When I try to run it as the user named "guest", I get an error saying that the password was incorrect. Could this have to do with the fact that my guest user has no password?

---

### Post by Jeremy23 on 2007-05-12
Okay, I haven't tested this either, but try this:

```

Cmnd_Alias      GUEST_CMDS = /usr/bin/network-admin

guest           ALL=(ALL) NOPASSWD: GUEST_CMDS

```

---

