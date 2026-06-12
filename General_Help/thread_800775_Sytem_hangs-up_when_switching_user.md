---
title: "Sytem hangs-up when switching user"
date: 2008-05-20
forum: General Help
---

### Post by milanvora2 on 2008-05-20
Hi,

I experienced yesterday the following problem:

- If I log on as User A , every thing works
- If i log on as User B everythign works
- If I try to switch users (System > Quit  > Switch user), the system hangs up (blank screen, keyboard hangs up)
- If I log out as user A and then log in as user B then everything works (don't remeber if this works all the time)

Can anyone give any pointers where I should start ?

---

### Post by Patb on 2008-05-20
Milanvora, I'm not sure whether this will show you anything but you could try to switch user from a terminal.  In Gnome, the command is 
```
gdmflexiserver
```
If you can see any output, it may give you a hint.  

Cheers, Pat.

---

### Post by skip mcshwang on 2008-05-20
This page might help you: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/112518](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/112518)

---

### Post by milanvora2 on 2008-05-20
tried: gdmflexiserver
the system hangs. what does that mean ?

now i'm going through the bug report. i hope to read and find something which solves this issue.

---

### Post by milanvora2 on 2008-05-22
I'm not getting any further.  my problem is still there.
anybody out there who could help ?

---

