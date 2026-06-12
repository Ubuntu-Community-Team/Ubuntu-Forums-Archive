---
title: "command line issues"
date: 2014-02-24
forum: General Help
---

### Post by setsuna2 on 2014-02-24
so, I'm using 12.04 LTS, an I can open ctrl+alt+f1 and type an all, however, it keeps telling me invalid login when I try, I've tried with/without capitals, tried computers name as login name, tried using both standard login password and bios password....nothing works.... am I missing something here? x.=.x

---

### Post by coldcritter64 on 2014-02-24
Your tty console login is your normal username and the password is your user login password.

Did you, when creating your account, use any capital letters or special (keyboard) characters in your username ? 

They would be sanitized by the system for use with a tty terminal and may be causing an authentication problem.

---

### Post by setsuna2 on 2014-02-24
*nods* aye, however as noted above, I attempted everything with no capitals, and with them, either way still says invalid login.

---

### Post by coldcritter64 on 2014-02-24
> **setsuna2 said:**
> *nods* aye,** however as noted above**, I attempted everything with no capitals, and with them, either way still says invalid login.

Yes I noted what you said above.

Post back the output of
```
whoami
```please.

TTY terminals have a known fault when it comes to usernames created with capitals/special characters originally (you attempting to capitize etc won't overcome an authentication fault caused as a result). They, tty terminals, are not as tolerant as a "normal" terminal emulator.

Yes or no. Did you **when originally making your account** include in your name a capital letter ? Remember when answering I know of a fault that it can possibly cause with authentication (_*which also seems to be what you are saying in your OP*_)

---

### Post by setsuna2 on 2014-02-24
yes I did, the first letter of my username, and there are 2 capitols in the password......though now I am a little confused, and have something else to attempt.... whoami returned ksi_setsuna, I don't remember putting that as my username, and it doesn't appear that way on my login screen, so I completely forgot that that was a possible name x.=.x

---

### Post by setsuna2 on 2014-02-24
got it, no caps in the UN but the password is still case sensitive, and it accepted the underscore to boot

---

### Post by coldcritter64 on 2014-02-24
You will always need to use a tty login with the username as returned by whoami and the password is fine as is.

This is different to your login screen as you've now noted, it would have stayed the same between the tty and login if you used all lowercase etc. Cheers.

---

