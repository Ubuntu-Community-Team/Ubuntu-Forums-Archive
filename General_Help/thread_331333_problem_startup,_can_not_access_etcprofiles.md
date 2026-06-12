---
title: "problem startup, can not access /etc/profiles/"
date: 2007-01-04
forum: General Help
---

### Post by _hawk_ on 2007-01-04
Hi!

I'vi got this problem that it's impossible for me to log on using my regular login session. If I try it says something about can not access /etc/profiles/ in the error log.

The error message is:
/etc/gdm/PreSession/Default: registering your session with wtmp and utmp
/etc/gdm/Presession/Default: ....
/etc/gdm/Xsession: Beginning session setup...
.: 106: Can't open /etc/profile

The thing is that I have installed ati drivers form the ati page manually, which did not work, and in an attempt to restore my computer back to the originally state, I eventually removed mesa (yeah I know, I'm stupid). I've reinstalled this, but it also removed lot's of other stuff in which I do not remember. If anyone has a single clue how I can fix this, I'd be forever grateful.

Also, I got the fglrx to finally work:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.6011 (8.28.8)


Hawk

---

### Post by steefjeqv on 2007-01-04
Hi,

I've done exactly the same thing.
You're not the only "stupid" around.
If I come up with a solution within the hour I'll let you know (otherwise it's bedtime for me).

Greetings,
Steven

---

### Post by taurus on 2007-01-04
What's the permission of /etc/profile?

Applications -> Accessories -> Terminal
```
ls -la /etc/profile
```

---

### Post by steefjeqv on 2007-01-04
Hi,

steven@flufje1:~$ ls -la /etc/profile
-rw------- 1 root root 369 2007-01-04 22:28 /etc/profile


Greetings,
Steven

---

### Post by taurus on 2007-01-04
> **steefjeqv said:**
> Hi,

steven@flufje1:~$ ls -la /etc/profile
-rw------- 1 root root 369 2007-01-04 22:28 /etc/profile


Greetings,
Steven

There you go.  Right now, only root can read and write to it and nobody else can't.  Therefore, you need to change the permission so you can read it when you log in.  From a terminal, run

```
sudo chmod 644 /etc/profile
```
Log out and back in again to see if you still have the problem reading /etc/profile.

---

### Post by steefjeqv on 2007-01-04
Hi Taurus,

Problem solved.
Thank you very much indeed !

Greetings,
Steven

---

### Post by taurus on 2007-01-04
Glad to hear that my little method solved your problem.

---

### Post by _hawk_ on 2007-01-04
wohoo! thanks mate... Worked for me to! And I feel even more stupid :)

---

### Post by taurus on 2007-01-04
> **_hawk_ said:**
> wohoo! thanks mate... Worked for me to! And I feel even more stupid :)

Another happy customer!!!  ;)

---

### Post by scotsboyuk on 2007-01-12
@taurus

I had the same problem as the OP, and your solution worked a treat. Thank you very much. :)

---

### Post by rodrigo666 on 2007-01-25
Thanks mate, I did the same stupid thing. That solved.

---

