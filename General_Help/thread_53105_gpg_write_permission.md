---
title: "gpg write permission"
date: 2005-07-30
forum: General Help
---

### Post by Bo Rosén on 2005-07-30
Not sure what is going on here. I decided to add an email addres to my gpgkey and that seems to have worked fine gpg --edit-key adduid but gpg is unable to save the changes. Should the pubring really be ownded by root? Or is this something to do with apt-get?

 ```
-rwxr-xr-x  1 brosen brosen   120 2004-01-29 12:01 gpa.con
-rw-r--r--  1 brosen brosen	91 2005-03-22 12:26 gpa.conf
-rwxr-xr-x  1 brosen brosen  8070 2004-01-07 12:14 gpg000.con
-rwxr-xr-x  1 brosen brosen  8068 2005-03-29 23:48 gpg.con
-rwxr-xr-x  1 brosen brosen  8069 2005-03-29 23:47 gpg.con~
-rwxr-xr-x  1 brosen brosen 12378 2004-01-29 12:01 pubri000.gpg
-rwxr-xr-x  1 root   root   21359 2005-07-30 10:13 pubring.gpg
-rwxr-xr-x  1 root   root   20038 2005-05-18 21:57 pubring.gpg~
-rwxr-xr-x  1 brosen brosen   600 2004-08-02 22:09 random_s
-rw-------  1 brosen brosen   600 2005-07-29 17:32 random_seed
-rwxr-xr-x  1 brosen brosen  1046 2004-01-29 12:01 secring.gpg
-rwxr-xr-x  1 brosen brosen  1520 2005-07-30 11:05 trustdb.gpg
brosen@Delirium:~/.gnupg$

```

---

### Post by bmontgom on 2005-07-30
root shouldn't own any of your gpg files.  Change the owner and group to "brosen" for all files and also change the permissions to 600.  You don't want anyone else to be able to view the files in .gnupg.  Be aware that this won't stop root from reading the files.

Run these commands in the .gnupg directory:
```

$ sudo chown brosen:brosen *
$ chmod 600 *
```

---

### Post by Bo Rosén on 2005-07-31
[QUOTE=bmontgom]root shouldn't own any of your gpg files. Change the owner and group to "brosen" for all files and also change the permissions to 600. You [/QUOTE]

Thanks. I thought I should do something like that but wasn't sure.

---

