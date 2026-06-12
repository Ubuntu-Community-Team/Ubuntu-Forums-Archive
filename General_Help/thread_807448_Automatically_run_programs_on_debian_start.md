---
title: "Automatically run programs on debian start"
date: 2008-05-25
forum: General Help
---

### Post by Roberto_Lapuente on 2008-05-25
Hi, I am trying to automatically start 3 python programs at the same time with debian(no gui) at startup. I also set up debian to log in automatically.

I tried adding them to "/etc/rc.local" but this won't start a program until the other one stops running and the idea is to have all 3 running all time.

I also tried to log in with different users in different terminals and run one program with each but that doesn't work either.

Please help.

---

### Post by Monicker on 2008-05-25
Did you try background them in /etc/rc.local?

```
program1 &
program2 &
program3 &
```

The ampersand will put each one in the background and proceed to the next.  Depending on the programs themselves, they may already have an option to run as a daemon in the background.

---

### Post by Roberto_Lapuente on 2008-05-25
thanks:) it worked

---

