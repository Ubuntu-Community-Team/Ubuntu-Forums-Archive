---
title: "Can't update, dpkg warning"
date: 2013-12-18
forum: General Help
---

### Post by jakefish on 2013-12-18
Hello,
I would greatly appreciate any help, i try to update with software updater and it doesnt work. So i try it through terminal and i get this error message

dpkg: warning: parsing file '/var/lib/dpkg/available' near line 36925 package 'erlang-snmp':
 `Depends' field, reference to `erlang-runtime-tools':
 version value starts with non-alphanumeric, suggest adding a space
dpkg: error: parsing file '/var/lib/dpkg/available' near line 36925 package 'erlang-snmp':
 'Depends' field, reference to 'erlang-runtime-tools': error in version: epoch in version is not number
E: Sub-process /usr/bin/dpkg returned an error code (2)


Can anybody help ?

thanks 

John

---

### Post by fantab on 2013-12-18
To fix this you have to delete/clear the file '/var/lib/dpkg/available' with the following :

    ```
$ sudo dpkg --clear-avail
```

   ... then rebuild the file using the command:

    ```
$ sudo apt-get update
```

To update:
```
sudo apt-get upgrade
```

---

### Post by jakefish on 2013-12-18
Thank you very much fantab, that appears to have worked

merry christmas

John

---

