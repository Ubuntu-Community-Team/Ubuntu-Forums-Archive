---
title: "issues with dbhelper*"
date: 2015-08-27
forum: General Help
---

### Post by balvarezpr on 2015-08-27
i am new to Linux but learning fast. I was insalling a copy of VLC and i rebooted the computer in the middle of the install. Ever since i am having an error:

The following packages have unmet dependencies:
 debhelper : Depends: dpkg-dev (>= 1.17.0) but it is not installed
E: Unmet dependencies. Try using -f.

i have tried different apt-get command with no luck. and other installs do not finish correctly or always display this error.

1) Can someone please explain to me what this package is?
2) How to fix this issue.

thanks in adavance for any help with the issue.

---

### Post by v3.xx on 2015-08-27
Try

```
sudo dpkg --configure -a
```

See if that will do anything.

---

### Post by flaymond on 2015-08-31
Run 

the command as suggested by v3.xx

If still not working, try this -

```
apt-cache show dpkg-dev
```

and post the outputs.

---

