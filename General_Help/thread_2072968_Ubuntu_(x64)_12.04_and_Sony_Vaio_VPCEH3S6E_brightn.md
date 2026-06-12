---
title: "Ubuntu (x64) 12.04 and Sony Vaio VPCEH3S6E brightness level"
date: 2012-10-18
forum: General Help
---

### Post by richard78917 on 2012-10-18
Hello,
I have a problem with brightness level on my Sony Vaio VPCEH3S6E, i installed Ubuntu here- dualboot with windows. Problem is that I can't set my brightness level- it is allways maximum.

Thank you for any ideas

---

### Post by pqwoerituytrueiwoq on 2012-10-18
out put of these commands
```
ls /sys/class/backlight/
ls /sys/class/backlight/*/

```

---

### Post by richard78917 on 2012-10-19
> **pqwoerituytrueiwoq said:**
> out put of these commands
```
ls /sys/class/backlight/
ls /sys/class/backlight/*/

```

Nothing  happens

---

### Post by pqwoerituytrueiwoq on 2012-10-19
they have to do something at the very least say no such file or directory

---

### Post by richard78917 on 2012-10-19
Ok sorry for my bad reply.

here is the screen, it says:
ls: it is not able to access to /sys/... : Directory or file does not exist

---

### Post by richard78917 on 2012-10-22
So you can't help me with my problem???

---

### Post by pqwoerituytrueiwoq on 2012-11-10
sorry lost this thread
you can try [xbacklight](apt:xbacklight)

---

### Post by rnerwein on 2012-11-11
> **richard78917 said:**
> Hello,
I have a problem with brightness level on my Sony Vaio VPCEH3S6E, i installed Ubuntu here- dualboot with windows. Problem is that I can't set my brightness level- it is allways maximum.

Thank you for any ideas

hi
i have 2 sony vaio laptops (pcg z...)  and on both the brightnes is set via Fn+F5 key.
may be this is the same at yours.
bye

---

### Post by richard78917 on 2012-11-20
> **pqwoerituytrueiwoq said:**
> sorry lost this thread
you can try [xbacklight]("apt:xbacklight")

That program doesn't work :(

> **rnerwein said:**
> hi
i have 2 sony vaio laptops (pcg z...)  and on both the brightnes is set via Fn+F5 key.
may be this is the same at yours.
bye

Thanks but that shortcut do nothing :(

So is there any hope to save my eyes?? :D or Windows is only solution?? :)

---

