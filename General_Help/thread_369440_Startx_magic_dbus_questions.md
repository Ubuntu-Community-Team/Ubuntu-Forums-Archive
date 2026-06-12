---
title: "Startx magic? dbus questions"
date: 2007-02-24
forum: General Help
---

### Post by tsg1zzn on 2007-02-24
Hi everyone
I have disabled GDM and enabled slim (simple login manager) by modifying the bootscripts. So far so good, but when I log in (xfce) programs complain about a missing dbus connection. When I log in with slim I have only one dbus-daemon running. If I kill slim, login from the console and then use startx I have two dbus-daemons and one dbus-launch running.

My questions:
1. Why isn't one dbus-daemon enough? (Do I really need *two*?)
2. What does dbus-launch do?
3. How to setup dbus without startx?
4. I suspect this is due to some magic going on when I type startx from the console (slim starts x directly without this script). If I find out how to setup dbus manually, will I still have other problems? I fear there's a lot of things going on inside that startx spaghetti.

I hope someone knows some of this!

---

### Post by yabbadabbadont on 2007-02-25
Make sure that slim is calling startxfce4 to launch xfce on login.

---

### Post by tsg1zzn on 2007-02-25
> **yabbadabbadont said:**
> Make sure that slim is calling startxfce4 to launch xfce on login.
Thanks, that worked. (I used xfce4-session before.)

---

