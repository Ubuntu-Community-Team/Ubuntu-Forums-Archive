---
title: "How to delete entries form environment var. $LANG?"
date: 2006-11-19
forum: General Help
---

### Post by disable2017July14 on 2006-11-19
Hi

Recently, I wanted to permanently add some jar-libraries for a java applet to the PATH variable. It worked, but now I've got a problem with the locale:

```
reni@ubuntu:~$ locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
<snip>
en_US.utf8
```
I found out that the added jar-libraries for some reason show up in $LANG!!

```
reni@ubuntu:~$ echo $LANG
en_US.UTF-8":/home/reni/GBI/googleapi.jar:/home/reni/GBI/httpunit.jar<snip>
```
So I wanted to remove these jar-libraries from the $LANG, I checked the follwing files but couldn't find the entries:

/etc/environment
/etc/profile
~/.bash_profile
~/.bash_rc

I'm using Edgy Eft, does it have something to do with the dash shell? How can I get rid of the enries in $LANG??

Thanks a lot for advise!!! Reni

---

