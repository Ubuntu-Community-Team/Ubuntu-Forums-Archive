---
title: "batch replace colons with dashes from folder names?"
date: 2014-10-07
forum: General Help
---

### Post by sohlinux on 2014-10-07
Hello, I want to batch replace colons : with dashes - in all folder names

eg. fred:tom will become fred-tom

eg. hello:you will become hello-you

how can I do this?

thanks

---

### Post by TheFu on 2014-10-07
```
rename 's/\:/\-/g' *
```
is the base. Add that to a **find** command and replace the wildcard with the found directory.

---

### Post by sohlinux on 2014-10-07
thanks but it doesnt work

---

### Post by TheFu on 2014-10-07
Well, it worked here.

t:4544/
became
t-4544/

If you want more help, please post the exact command and results.

---

### Post by papibe on 2014-10-07
Hi sohlinux.

If TheFu's suggestion didn't work, my guess either you needed a recursive renaming, or the character is not actually a regular ASCII colon, but an extended character.

To check what character really is try this:
```
echo fred:tom | od -a
```
but use Bash completion (tab key) to get the actual name of the file.

Let know how that goes.
Regards.

---

### Post by sohlinux on 2014-10-07
actually it worked, it was a semi colon. thanks :)

---

