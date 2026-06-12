---
title: "su password [Resolved]"
date: 2007-05-01
forum: General Help
---

### Post by fparker on 2007-05-01
Hello all
I just install two weeks ago and am trying out some of the commands on tghe system.  I am trying out the su command and its asking for a password.  I don't remember entering a password during installation.  Is there a default?  Am I going to have to re-install the whole system?

Frank

---

### Post by aysiu on 2007-05-01
There is no *su* for a root user, and it's not necessary. Read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by soulfly7x on 2007-05-01
don't you use a password in the login screen? It should be that. If you somehow bypass the login screen then I just dunno. :confused:

---

### Post by fparker on 2007-05-01
Hello all,
I installed my system twos ago and am trying out some of the commands.  Trying out the su command and it's asking for a password.  I don't remember entering a password during installation.  Is there a default.  Am I going to have to re-install the complete system?

Frank

---

### Post by aysiu on 2007-05-01
> **soulfly7x said:**
> don't you use a password in the login screen? It should be that. If you somehow bypass the login screen then I just dunno. :confused:
If you type *su* (or *s*witch *u*ser)  without specifying what user to switch to, the assumed user is *root*. Root logins are disabled in Ubuntu by default--they're also completely unnecessary.

The link above explains more: the reasons for using *sudo* instead, the pros and cons of each model, how to return to a traditional root/user model.

---

### Post by nanotube on 2007-05-01
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

it's asking for your user password...

---

### Post by Jeff24K on 2007-05-01
By default the root account login is disabled on Ubuntu machines. Using 'su' is prompting you for a password that doesn't exist. The "standard" way to perform administratice tasks is with 'sudo'. If you want to become root on a semi-permanent basis use...

```
sudo -i
```

The password is asks for will be your normal user password.

---

### Post by fparker on 2007-05-02
OK.  Using sudo works with my login password.  I'm doing a tutorial I purchased and it mentioned su, which I now see I don't need.  Thanks.

---

### Post by zvacet on 2007-05-02
Read carefuly this page

[https://help.ubuntu.com/community/LostPassword]("https://help.ubuntu.com/community/LostPassword")

---

### Post by fparker on 2007-05-02
Got it (phew!!!) 
Thanks,

Frank
Thought for a moment I didn't write something down and would have to re-install...

---

### Post by fparker on 2007-05-02
Read the article and now do understand.  Using sudo and my user password.  Thanks.

---

