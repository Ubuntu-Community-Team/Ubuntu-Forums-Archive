---
title: "authentication issues wont let me install new software"
date: 2018-08-21
forum: General Help
---

### Post by seekertom on 2018-08-21
ubuntu 18.04.1 64 bit amd pc
I'm trying to install pinta, among other apps, and get this message: authentication is required to install software.
incorrect permissions on /usr/lib/policykit-1/polkit-agent-helper-1 (needs to be setuid root)

I set this pc up from scratch, new hd, fresh install ubuntu from iso dvd, single user on pc.
Mostly things running ok, but issues like this driving me nutz.

I hope you can help me correct this core issue so I can get back to happily installing my apps, printers etc.
thanks!
st

:confused:

thanks to all for the help. all these issues have been corrected. 
st!

---

### Post by sisco311 on 2018-08-21
Did you try to alter the owner/permissions of any system file or directory?

The error message indicates that the permission of the polkit-agent-helper-1 file is not correct. What is the output of:
```
ls -l /usr/lib/policykit-1/polkit-agent-helper-1
```

---

### Post by seekertom on 2018-08-21
-rwxr-xr-x 1 root root 14328 Jul 13 07:42 /usr/lib/policykit-1/polkit-agent-helper-1

---

### Post by seekertom on 2018-08-21
to add to my dilemma, this is what i get when trying to install pinta (and others) on a second, nearly identical pc...
error while installing package: installed shim-signed package post-installation script subprocess returned exit error stastus 1.

any help sure appreciated!
st

---

### Post by seekertom on 2018-08-21
add this info, on 1 st pc, -rwxr, but on 2nd pc, one that doesnt complain about permissions, that sequence is -rwsr...

i believe the rw is read write, but the rest i dont understand...

---

### Post by sisco311 on 2018-08-21
> **seekertom said:**
> -rwxr-xr-x 1 root root 14328 Jul 13 07:42 /usr/lib/policykit-1/polkit-agent-helper-1

The error message is right. Not sure why and how it happened but the file is not longer setuid root. To make it setuid root, run:

```
sudo chmod 4755 /usr/lib/policykit-1/polkit-agent-helper-1
```

> **seekertom said:**
> add this info, on 1 st pc, -rwxr, but on 2nd pc, one that doesnt complain about permissions, that sequence is -rwsr...

i believe the rw is read write, but the rest i dont understand...

The community Wiki is a relatively good start to learn about Linux/Unix file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

EDIT: And of course, you should also check out: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)



> **seekertom said:**
> to add to my dilemma, this is what i get when trying to install pinta (and others) on a second, nearly identical pc...
error while installing package: installed shim-signed package post-installation script subprocess returned exit error stastus 1.

any help sure appreciated!
st

Probably not related.

---

### Post by seekertom on 2018-08-23
i ran this --sudo chmod 4755 /usr/lib/policykit-1/polkit-agent-helper-1   in terminal, and no longer get permission error... now I get this issue..

unable to install Pinta: e:dpkg was interrupted, you must manually run 'dpkg --configure-a' to correct the problem.

(one day I'll be good at this...)
thanks, st

---

### Post by sisco311 on 2018-08-23
Still not sure what happened to your system, but the error message is self explanatory. You have to run:
```
sudo dpkg --configure -a
```
This should solve your problem.  If you get any error messages please post them here.

---

