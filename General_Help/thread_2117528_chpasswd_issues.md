---
title: "chpasswd issues"
date: 2013-02-18
forum: General Help
---

### Post by enenalan on 2013-02-18
Just starting to dig into this operating system and I'm trying to find a way to non-interactively change user passwords in Ubuntu Server 12 LTS (I'll be using it in a script later, so passwd isn't going to work for me.)

Right now, I'm doing this - 
```

sudo echo 'username:password' | chpasswd

```It tries, but it keeps coming back with this - 
```

Changing password for username.
chpasswd: (user username) pam_chauthtok() failed, error:
Authentication token manipulation error
chpasswd: (line 1, user username) password not changed
```Any ideas?  I tried it with all of the switches too just out of frustration....

---

### Post by steeldriver on 2013-02-18
you're giving elevated permissions to the 'echo' (which doesn't need them) but not to the 'chpasswd' (which does)

---

### Post by enenalan on 2013-02-18
Duh.  I figured the sudo privilege would propagate down the pipe...  Newbie idiocy!  

Thanks!!!

---

