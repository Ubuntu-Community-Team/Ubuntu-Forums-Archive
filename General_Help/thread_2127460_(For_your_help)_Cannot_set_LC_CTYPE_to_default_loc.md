---
title: "(For your help) Cannot set LC_CTYPE to default locale: No such file or directory..."
date: 2013-03-20
forum: General Help
---

### Post by killeo on 2013-03-20
[B]locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory[/B]

1. try this:
 [http://ubuntuforums.org/showthread.php?t=1720356](http://ubuntuforums.org/showthread.php?t=1720356)
2.(worked for me): [URL="http://itblog.su/cannot-set-lc_ctype-to-default-locale.html"]
[/URL][http://itblog.su/cannot-set-lc_ctype-to-default-locale.html](http://itblog.su/cannot-set-lc_ctype-to-default-locale.html)
>  sudo localedef en_US:en -i en_US -fUTF-8 
> sudo update-locale LC_ALL=en_US.UTF-8

---

