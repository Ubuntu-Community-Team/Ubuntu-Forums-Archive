---
title: "How to keep Ubuntu from changing /usr/sbin/sendmail link?"
date: 2013-07-18
forum: General Help
---

### Post by ekool on 2013-07-18
I have quite a few Ubuntu servers deployed (10.04, 12.04). On these servers, I install manually qmail and some other mail packages. They work great and everything is fine. I manually change the /usr/sbin/sendmail into a symlink and point it to /var/qmail/bin/sendmail.

However, sometimes when I do an update of the system, Ubuntu over-writes this to its own wrapper, or replaces it with a sendmail binary, or sometimes points it to exim4...

How can I run a command that tells the system to never touch it... I've thought about making the file immutable, but I assume there is a more elegant way by installing some type of mail stub?

---

### Post by ekool on 2013-07-19
Is there a more appropriate section I should ask this question in?

---

### Post by Cheesehead on 2013-07-19
Well, I don't use qmail, but the file /usr/sbin/sendmail is installed by the postfix package.

Do you have postfix installed? If so, do you really need it? You seem to be using qmail as your mta.

Every time postfix updates, it will indeed overwrite your symlink. It's possible to pin a package version so it does not update...but that may not be the best solution.

---

### Post by dcstar on 2013-08-04
```
man update-alternatives
```

---

