---
title: "How to check the password or login access to root and other accounts are disabled."
date: 2014-05-25
forum: General Help
---

### Post by vRanger on 2014-05-25
On Ubuntu, I understand root account is there, but the ability to su or login with root is disabled.  How do I verify that is the case?  I also want to check that is the case for some other particular user accounts, like sshd as well.

I did find this in the Ubuntu documentation for sudo, which is used to disable the ability to root login if it was enabled despite numerous warnings against it.
> [COLOR=#333333][FONT=UbuntuMono]sudo passwd -dl root[/FONT][/COLOR]
However this is not helping, because I do not want to simply make sure it is disabled, I want to know what the current state is.

---

### Post by bapoumba on 2014-05-25
```
bapoumba@SonyBlue:~$ sudo grep "root" /etc/shadow
root:!:16187:0:99999:7:::
```

A ! means the account is disabled. [http://linux.die.net/man/5/shadow](http://linux.die.net/man/5/shadow)
> If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means). 

---

### Post by vRanger on 2014-05-25
Thank you!  Don't know why that had to be so hard to find with Google, but you sure helped.

---

### Post by bapoumba on 2014-05-26
You are welcome, please mark your thread as solved (under Thread Tools), thanks :)

---

