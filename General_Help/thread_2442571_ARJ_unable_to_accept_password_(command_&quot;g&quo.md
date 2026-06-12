---
title: "ARJ unable to accept password (command &quot;g&quot;)"
date: 2020-05-04
forum: General Help
---

### Post by Alistair George on 2020-05-04
File Roller crashes with very large number of files so I use arj with bash. Problem is as follows eg:
alistair@alsE590:~$ arj a -r -gmypass dropbox_d5m5y20.arj Dropbox/*
which creates arc with password of mypass; but when I go to extract and enter the password, its not accepted and repeats password request.
so I make same arc with this command:
alistair@alsE590:~$ arj a -r -g? dropbox_d5m5y20.arj Dropbox/*^C

which prompts for the password before build but even so, I still get the continuous request for wrong password.

Any ideas?

---

