---
title: "copy using wild cards"
date: 2007-11-14
forum: General Help
---

### Post by rgfrancis on 2007-11-14
I would like to copy everything in a folder over to another folder. I tried:

sudo cp *.* /var/www and that didn't work.

Just learning the basics now

---

### Post by JasonF on 2007-11-14
What output do you get? The command should work, but typically you would simply type * instead of *.*, unless you only plan to copy files with periods in their name. Also if you plan to copy directories you should add the -r (Recursive) switch.

---

### Post by rgfrancis on 2007-11-14
That worked. Thanks

---

