---
title: "Problem instaling Screens"
date: 2021-12-23
forum: General Help
---

### Post by pwnyhorst on 2021-12-23
Hello,
I am new to hosting servers on linux and I got a problem.
I need to install screens so I can run a certain piece of software in the background.
The only problem is that everytime I try to install screens via this command

```

 [B]$ apt-get install screen lib32gcc1
[/B]
```

I get the following error message

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

I have, in my very limited time on linux, not seen this and I don't understand what this means.
The server is running regular Ubuntu 20.04 and should be fully updated.

---

### Post by howefield on 2021-12-23
So what happened when you run the command asked of you?

---

### Post by pwnyhorst on 2021-12-23
Nothing, atleast from what I can tell. I don't even know what the command means.
Also happened when I tried to install EMACS editor

---

### Post by pwnyhorst on 2021-12-23
So apparently my server decide to crash the first time and my Program didn't notice it. Tried it again and now it works. Sorry for bothering anyone

---

