---
title: "Enter the administrative password in Raring Ringtail"
date: 2013-06-13
forum: General Help
---

### Post by Canaryguy on 2013-06-13
Hello,

Not so long time ago I have noticed that when I want to execute a program that requires administrative privileges a new window appears with a box to enter the password, and a checkbox (unmarked by default) that lets you choose between "Save for this sesion" and "Save in the keyring".

The problem is that my administrative password is recognized as wrong. Let's say I want to execute "Bleachbit (as root)". The window appears asking for my password but it says it is wrong. On the other hand if I execute Bleachbit through the Terminal using my administrative password I can open the program.

Anybody having the same problem?

---

### Post by papibe on 2013-06-13
Hi  Canaryguy.

It looks like a miss configured gksudo. Open a terminal and run:
```
gksu-properties
```
Then make sure the 'Authentication mode' is set to 'sudo'.

Let us know if that helps.
Regards.

---

### Post by Canaryguy on 2013-06-13
> **papibe said:**
> Hi  Canaryguy.

It looks like a miss configured gksudo. Open a terminal and run:
```
gksu-properties
```
Then make sure the 'Authentication mode' is set to 'sudo'.

Let us know if that helps.
Regards.

Thank you very much! 

Yes, as you said, it was not configured correctly. When I used "gksu-properties" I saw that the Authentication mode was set to "su" instead of "sudo".

Now the problem is solved. Thank you very much papibe!

---

