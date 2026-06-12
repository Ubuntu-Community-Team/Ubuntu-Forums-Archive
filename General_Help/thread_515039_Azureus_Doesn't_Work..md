---
title: "Azureus Doesn't Work."
date: 2007-08-01
forum: General Help
---

### Post by Sayers on 2007-08-01
```
sayers@Desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb484e172, pid=11858, tid=3085077392
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid11858.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

The GUI loads then closes.

---

### Post by OoooMatron on 2007-08-01
try updating to the new JRE (use automatix) and failing that delete your .azurues folder in your home directory(or rename it).

---

### Post by Sayers on 2007-08-01
I have the latest JRE .

---

### Post by smileysteve on 2007-08-01
I have experienced this same issue many times, most of the times on a crash of somesort (like when I was trying to use i2p a lot) azureus wouldn't launch again. I found that if you delete ~/.azureus/logs/ you can often run the software again.

Stephen

---

### Post by LMP900 on 2007-08-01
Here's a post that helped me resolve a similar issue:

[http://ubuntuforums.org/showpost.php?p=1680674&postcount=13](http://ubuntuforums.org/showpost.php?p=1680674&postcount=13)

---

### Post by OoooMatron on 2007-08-02
> **Sayers said:**
> I have the latest JRE .

did you remove the azureus folder as well? did it help?

---

### Post by OoooMatron on 2007-08-02
> **LMP900 said:**
> Here's a post that helped me resolve a similar issue:

[http://ubuntuforums.org/showpost.php?p=1680674&postcount=13](http://ubuntuforums.org/showpost.php?p=1680674&postcount=13)

I'm surprised this is still an issue. I had this exact problem a long long time ago and the new beta jar file also fixed my issue with azureus shutting down. been fine on feisty though,.

---

