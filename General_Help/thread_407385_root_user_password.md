---
title: "root user password"
date: 2007-04-12
forum: General Help
---

### Post by Petester on 2007-04-12
I have set my password to (lets say) "1234567" (without quotes) and it worked with all sudo's.
however it didnt work with su's.... It says Authentication failure all time... what would be my password?

---

### Post by dcstar on 2007-04-12
> **Petester said:**
> I have set my password to (lets say) "1234567" (without quotes) and it worked with all sudo's.
however it didnt work with su's.... It says Authentication failure all time... what would be my password?

You have to enable the root account first to use su:
```
sudo passwd root
```
Be warned that root is disabled by default as a security measure.

---

### Post by firebadger on 2007-04-12
su (switch user) would require that user's password.  Without a username argument, it assumes root so you would need to provide that one.  However, by default in Ubuntu the root account does not have a password set and so you cannot log in as root.
Round here, this is generally considered a good thing and you should just use sudo (switch user do - I think) for carrying out admin tasks.  This requires your password.

---

### Post by firebadger on 2007-04-12
You can also become root without setting a password by running the following and entering your own password.

```
sudo su -
```

---

### Post by Petester on 2007-04-12
Ah thanks firebadger, that worked:D

---

### Post by TheWizzard on 2007-04-12
> **firebadger said:**
> You can also become root without setting a password by running the following and entering your own password.

```
sudo su -
```

this is more elegant: 
```
sudo -s
```

information about su and sudo can be found here: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

