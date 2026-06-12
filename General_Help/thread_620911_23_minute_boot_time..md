---
title: "23 minute boot time."
date: 2007-11-23
forum: General Help
---

### Post by tomcullpepper on 2007-11-23
I know I'm not uising Ubuntu, but the Sabayon scene is dead, or Italian, and I only speak spanish and english,  Anyway, I just booted my computer in Sabayon and it took 23 minutes exactly, why is this?  Isn;'t Linux faster than windows?

Vista boots in less than 2...

---

### Post by quinnten83 on 2007-11-23
you can start by checking in your sessions manager (or equivalent) what is starting up.
Perhaps there is a program that got stuck, and that is why it is taking so long.

---

### Post by tomcullpepper on 2007-11-23
> **quinnten83 said:**
> you can start by checking in your sessions manager (or equivalent) what is starting up.
Perhaps there is a program that got stuck, and that is why it is taking so long.

Someone said something about boot times getting faster as you go, I know it was like that for Vista, but it never took more than 3 minutes to boot anyway.  How do I check my sessions manager?

---

### Post by por100pre1 on 2007-11-23
> **tomcullpepper said:**
> Someone said something about boot times getting faster as you go, I know it was like that for Vista, but it never took more than 3 minutes to boot anyway.  How do I check my sessions manager?

Try this:

```
gnome-session-properties
```

BTW, I think you should give Ubuntu 7.04 Feisty a try. It is very stable. :-k

---

### Post by indosupremacy on 2007-11-23
well....very strange i thing......maybe  be something in your xorg conf broooo

---

### Post by xeth_delta on 2007-11-23
> **tomcullpepper said:**
> I know I'm not uising Ubuntu, but the Sabayon scene is dead, or Italian, and I only speak spanish and english,  Anyway, I just booted my computer in Sabayon and it took 23 minutes exactly, why is this?  Isn;'t Linux faster than windows?

Vista boots in less than 2...

Can you confirm that it is taking that much all the time? Maybe a disk verification was taking place. They can be scheduled to run every time a number of boot cycles has been performed.

Depending on your partitions dimensions, it might take a while.

Xeth

---

