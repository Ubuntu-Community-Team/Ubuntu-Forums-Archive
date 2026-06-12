---
title: "[SOLVED] Sudo command where are settings about password stored"
date: 2008-02-06
forum: General Help
---

### Post by abcuser on 2008-02-06
Hi,
using Ubuntu 7.10 Desktop when executing sudo commands (e.g. sudo cat /etc/passwd) system asks for my password. I am used to Suse Linux where system asks for root!!! password (not my password but root password). I would like to know where is this settings stored. I looked into /etc/sudoers but there is no such info in this file. Any idea where to set what password (my password or root) must be typed when sudo command is executed?
Thanks,
Abcuser

---

### Post by Seisen on 2008-02-06
The password sudo asks for is the same password that you would have setup when you installed Ubuntu. You can also change your password by going to System>Admnistration>Users and Group, then selecting you user and clicking on properties.

---

### Post by cdenley on 2008-02-06
I believe you can do this with "sudo visudo" by adding "targetpw" to the "Defaults" line. MAKE SURE YOU SET A ROOT PASSWORD FIRST! 
```

sudo passwd

```
I'm not going to test this because I don't want to set a root password.

---

### Post by lsavidge on 2008-02-06
Hi,

Just type in:

sudo passwd root

type in YOUR password and it will then prompt you for a new ROOT password.

Cheers,

Lee

---

### Post by seventhc on 2008-02-06
It is not recommended to set the root password, it is locked by default in ubuntu. Using sudo allows you to make necessary system changes.

---

### Post by bodhi.zazen on 2008-02-06
Ubuntu uses sudo :

sudo:

	[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And gksudo for graphical applications : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by abcuser on 2008-02-06
> **cdenley said:**
> I believe you can do this with "sudo visudo" by adding "targetpw" to the "Defaults" line. MAKE SURE YOU SET A ROOT PASSWORD FIRST! 
```

sudo passwd

```
I'm not going to test this because I don't want to set a root password.
cdenley,
that is the answer I was looking in. In my /etc/sudoer file on Suse Linux there are following lines:
```

#When configuring sudo, delete the two following lines:
Defaults targetpw    # ask for the password of the target user i.e. root
ALL ALL=(ALL) ALL # WARNING! Only use this together with 'Defaults targetpw'!
```

So adding this two lines to /etc/sudoer adds full permissions to anyone on computer, but root password is required.

Thanks, now I understand why Suse Linux has this root-password in sudo as default. When sudo is configured this two lines should be deleted.

Thanks,
Abcuser

---

