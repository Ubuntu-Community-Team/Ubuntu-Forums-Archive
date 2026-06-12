---
title: "postfix file missing"
date: 2008-02-26
forum: General Help
---

### Post by artesian_spring on 2008-02-26
I've been trying to use the command line mail utility, but it keeps giving an error message:
> send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75

I tried creating a symbolic link using:
```
sudo ln -s /usr/share/postfix/main.cf.dist /etc/postfix/main.cf
```
This changed the error message to:
> send-mail: fatal: bad string length 0 < 1: setgid_group = 
Can't send mail: sendmail process failed with error code 75

Any suggestions? I'd like to eventually get the mail utility set up to send automated messages to my hotmail account. Is that even possible?

Thanks

---

### Post by dcstar on 2008-02-27
> **artesian_spring said:**
> I've been trying to use the command line mail utility, but it keeps giving an error message:

I tried creating a symbolic link using:
```
sudo ln -s /usr/share/postfix/main.cf.dist /etc/postfix/main.cf
```
........

The postfix package in the repositories installs all required files in all the correct places, did you install this package?

---

