---
title: "Here's a daft one"
date: 2007-03-07
forum: General Help
---

### Post by daveclayton on 2007-03-07
Just a quick question:

In Ubuntu, the root password is not set (or isn't documented), and everything is supposed to go via sudo.

So....

...what password do you put in when booting in recovery/single user mode?  It's supposed to be the root password.

Does this mean that for every machine that I may possibly ever want to recover data from in the event of a failure needs a root password explicitly set (which seems to me to defeat the idea behind not having the root password in the first place...)

Ta

---

### Post by Kateikyoushi on 2007-03-07
It did not ask me for root passwd as I remember when I tried single user mode, did you try your user passwd ?

---

### Post by taurus on 2007-03-07
If you boot into recovery mode, it will boot directly into a prompt as root.  It shouldn't ask for your root password unless you have created one before.

---

### Post by der_joachim on 2007-03-08
What Taurus said. Additionally: if you want to use your root password, all you have to do, is a ```
sudo passwd
```

---

### Post by daveclayton on 2007-03-08
Daft it is, then.  A root password must have been set at some point, guess I'll have to scratch my head a bit and see if I can remember that password.  Or just chroot from a boot floppy :)

Thanks,
David

---

