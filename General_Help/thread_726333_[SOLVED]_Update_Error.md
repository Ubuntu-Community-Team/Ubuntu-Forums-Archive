---
title: "[SOLVED] Update Error"
date: 2008-03-16
forum: General Help
---

### Post by LLn00bJ on 2008-03-16
7.10 installed on MS virtual PC on my E: hard drive on a vista machine for testing purposes everything runs fine works ok.
Go to get updates they are all there etc and it installed some but now it just keeps giving this message over and over again.
E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache0->open()failed,please report.
I manually run dpkg --configure -a says I need superuser privelges.
So I am reporting this. :D Other than that its all good. :)

---

### Post by bapoumba on 2008-03-16
Please try:
```
sudo dpkg --configure -a
```

---

### Post by LLn00bJ on 2008-03-16
Thankyou for your help.
That ran through and checked them all only gave one error for libpng12-0.
Then I ran the updates thing again and it installed them all.:guitar:

---

