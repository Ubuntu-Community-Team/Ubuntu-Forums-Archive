---
title: "Samba password help needed!"
date: 2014-01-31
forum: General Help
---

### Post by javajeff1 on 2014-01-31
I accidently created a root password with:
[COLOR="#FF0000"]smbpasswd -a[/COLOR]
by omitting the username.

The message was user root was created.

I then disabled by using
[COLOR="#FF0000"]smbpasswd -d root[/COLOR]

I then correctly set up my desired username and password correctly.

I cannot delete the root user that I created with:

[COLOR="#FF0000"]smbpasswd -x root[/COLOR]

Is this going to be a problem?  Is there a security issue?  Thanks!

---

### Post by deadflowr on 2014-01-31
Shouldn't be any problem.
All you did was give make an smbpassword for root.
root already exists as a user.
smbpasswd and passwd aren't the same thing.

---

### Post by javajeff1 on 2014-02-01
That is what I figured.  Thanks!

---

