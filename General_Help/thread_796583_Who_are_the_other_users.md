---
title: "Who are the other users?"
date: 2008-05-16
forum: General Help
---

### Post by achelis on 2008-05-16
Hi.

Still fairly new to Ubuntu and trying to learn.

Having just learned the uptime command I tried and got
```

 20:54:34 up  3:27,  3 users,  load average: 0.02, 0.07, 0.03

```

Which confuses me a bit - though I'm sure there is a reasonable explanation and I'm hoping someone can give it to me :)

Thanks

---

### Post by gareth_005 on 2008-05-16
Probably yourself, try the 'who' command :)

---

### Post by pointone on 2008-05-16
"users" is misleading. All three could potentially be the same user. Every X login counts as 2 users, FYI.

Try the "who" command.

---

### Post by defishguy on 2008-05-16
You can use the **who** command to see who happens to be logged on to your computer.

You are probably going to find your user name twice in the list.  The first time will mention something about tty/7 (that is the GUI) and another instance claiming that your are logged on tty/0 (command line) too.  This is normal because effectively when you open the terminal you are logging in a second time.

The third user might be any number of things.  Please post the output of the **who** command and we can help you out.

---

