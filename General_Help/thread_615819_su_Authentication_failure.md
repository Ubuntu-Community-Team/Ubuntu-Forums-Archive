---
title: "su: Authentication failure"
date: 2007-11-17
forum: General Help
---

### Post by warjim on 2007-11-17
Hi.

I have noticed that some utility programs do not work properly unless I am "Root User"

I tried the SU command in the terminal, but it asks me for a password that I was NOT asked to set. My user password does not work, which was set during installation.

Help!??

Thanks,
Jim

---

### Post by meatpan on 2007-11-17
Hello Jim,

Can you post the command you tried to run, and the associated error output?

---

### Post by Craigus on 2007-11-17
If you do:> sudo -i
you will get to a root prompt.> exit
will get you out.

---

### Post by warjim on 2007-11-17
I am trying to run QTParted (partition program). And when launched it says "No device found. Maybe you are not using root user?"

I tried the sudo qtparted command in the terminal and it does work, just not quite the way I want it too.

---

### Post by Craigus on 2007-11-17
It may be quicker and simpler to download and use the Gparted Live CD:

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by TNakos on 2007-11-17
tri going system>administration>users and groups>          then click on the root name and go down to password and set the one you want.

---

### Post by blaster32 on 2007-11-17
You cannot switch user to root if you dont have a password set for that user. its a safety precaution. to set a password for your root user use

```

sudo passwd

```

---

### Post by Exom on 2008-03-18
> **blaster32 said:**
> You cannot switch user to root if you dont have a password set for that user. its a safety precaution. to set a password for your root user use

```

sudo passwd

```

Thanks

---

### Post by yodna on 2008-05-25
recalling this thread, i tried creating a new password but still authentication failue on su. need help.:(

---

### Post by aysiu on 2008-05-25
There's no need to *su*

```
sudo -i
``` will make you root.

If you, like the OP, are trying to run something like QTParted or GParted, the command should be ```
kdesu qtparted
``` or ```
gksudo gparted
```

---

### Post by cssanyi on 2008-05-26
I had the same problem.
I did this to set a password for root:

1 Restart your PC
2 At boot choose Ubuntu Recovery mode
3 (if you use Hardy the next step is to choose the root shell)
4 now you are logged in as root, so type "passwd" and it will ask you to type a new password for the root.

It worked fine for me. Hope, I could help. :lolflag:

---

### Post by aysiu on 2008-05-26
> **cssanyi said:**
> I had the same problem.
I did this to set a password for root:

1 Restart your PC
2 At boot choose Ubuntu Recovery mode
3 (if you use Hardy the next step is to choose the root shell)
4 now you are logged in as root, so type "passwd" and it will ask you to type a new password for the root.

It worked fine for me. Hope, I could help. :lolflag:
Completely unnecessary to set a root password. But even if you do, there's absolutely no need to boot into recovery mode to do so.

---

### Post by Lakjin on 2008-07-23
> **cssanyi said:**
> I had the same problem.
I did this to set a password for root:

1 Restart your PC
2 At boot choose Ubuntu Recovery mode
3 (if you use Hardy the next step is to choose the root shell)
4 now you are logged in as root, so type "passwd" and it will ask you to type a new password for the root.

It worked fine for me. Hope, I could help. :lolflag:

sudo passwd

works fine dood.

---

