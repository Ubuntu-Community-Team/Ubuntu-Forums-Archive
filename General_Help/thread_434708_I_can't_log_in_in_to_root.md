---
title: "I can't log in in to root"
date: 2007-05-06
forum: General Help
---

### Post by Ioky on 2007-05-06
sometime the system can't accept my pass word for some reason, I am pretty sure the one i type in is the right one. like one time, i try to adjust my clock right after i just finish adjusting it. I can't log in anymore. it keep give me a failure error. it happen in sell-konsole too

---

### Post by mdwuznik on 2007-05-06
Are you able to login as a normal user ?
If yes, try _sudo_passwd_root_, if you want to change the root password (and enable the root account if it's in default, off state).

Cheers
Micha&#322;

---

### Post by hartz on 2007-05-06
This may be a sudo "timestamp" problem.

When you adjusted the time, if you set it backwards, you may get an error saying "Timestamp too far in the future".

To overcome this, open a new terminal without closing the other ones, because sudo tracks the timestamps by session, and a session is basically tied to the terminal tty number.

So if this is your situation then all you need to do is open a new terminal, then run commands in this session to get sudo once again to prompt and accept your password.

There may be other possible scenarios - if the above is not what you are experiencing, please give more detail like what commands you are entering and accurate error messages you see.

---

### Post by FITorion on 2007-05-09
> **mdwuznik said:**
> Are you able to login as a normal user ?
If yes, try _sudo_passwd_root_, if you want to change the root password (and enable the root account if it's in default, off state).

Cheers
Micha&#322;

how would one turn it off again after doing this?

---

