---
title: "How can I add users without requiring interaction?"
date: 2008-03-17
forum: General Help
---

### Post by awmcclain on 2008-03-17
I'm writing setup scripts to be invoked on brand new installations of Ubuntu, and I want to be able to create a small set of users on each new machine.

Unfortunately, I can't have any interaction (because it breaks the tool I'm using to administer the new machines). 

So: how do I add new users (with passwords) without any interaction?

I've got the adding down with ```
adduser --adduser username --gecos '' --disabled-login
``` but I can't figure out how to change the password (since passwd on 7.10 doesn't support --stdin.)

Or is there a way to crypt a password and somehow pass it into useradd, making sure that useradd does the proper things with UID and GID that adduser does?

Extremely frustrated,
a

---

### Post by jken146 on 2008-03-17
I think it's a security feature that passwd doesn't support stdin.  You might find it very difficult to get around this.

The command *useradd* with all its options will do most of the things you want, I believe.

---

### Post by awmcclain on 2008-03-17
Is there anything special I need to do make sure to do using useradd that is done automaticall with adduser?

---

### Post by PointyWombat on 2008-03-17
Hi awmcclain,

In order automate the creation a passworded account, you can use the **mkpasswd** command in conjunction with **useradd.**

In essence, you need to feed **useradd** with the password hash (which it stores in /etc/shadow) using the '**-p**' switch. To derive a hash from your desired password, you use **mkpasswd.**

So, for example:
```

sudo useradd testuser -p `mkpasswd -H md5 Password1234`
su - testuser
Password: Password1234
No directory, logging in with HOME=/

```

Running **mkpasswd** by itself will produce whatever style hash you need. Most Linux systems today use MD5 style hashes (the** -H md5** switch), which can be identified by the leading** $1$** characters if you  look at the /etc/shadow file. (You need to be root to see the /etc/shadow file).

Hope this helps.

PointyWombat

---

