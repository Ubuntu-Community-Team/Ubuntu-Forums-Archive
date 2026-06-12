---
title: "ubuntu hang on black screen"
date: 2013-01-08
forum: General Help
---

### Post by anime19861 on 2013-01-08
i install ubntu 12.10 
Successfully
but after Installation twinhan 1025 ubntu hang on black screen and cant log into system

---

### Post by Bucky Ball on 2013-01-08
Welcome to the forums.

Did it work when you tried Ubuntu from the LiveCD, if you did try it prior to installing?

At boot, when you see the list of kernels to boot, choose the top one, hit 'e' to edit, find the line that ends in 'quiet splash' or either of those words and add 'nomodset'.

Follow the instructions at the bottom of that page to save changes and continue with boot.

What happened?

---

