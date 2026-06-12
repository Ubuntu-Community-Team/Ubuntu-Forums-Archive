---
title: "ssh issue"
date: 2005-07-04
forum: General Help
---

### Post by djpenguin on 2005-07-04
I've got openssh server and client installed, but I can't seem to start the service

I run the following command:

```
/etc/init.d/ssh start
```

and get a [fail] message every time.

This is kind of a major pain, because the machine in question is a laptop I'm setting up for a friend, and I'd much rather do it remotely over ssh from my desktop machine.

Any help would be greatly appreciated.

---

### Post by adwait on 2005-07-04
run rcconf to make sure u rnt running it at startup itself? if it is already running, it says "fail"

---

### Post by djpenguin on 2005-07-05
Duh....

It's in runlevel 3.

Thanks.

---

