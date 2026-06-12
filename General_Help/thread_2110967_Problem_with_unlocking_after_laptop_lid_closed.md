---
title: "Problem with unlocking after laptop lid closed"
date: 2013-01-31
forum: General Help
---

### Post by DrScum on 2013-01-31
ubuntu 12.04 LTS on a Dell vostro 1520. Recently switched to nouveau display driver since the NVIDIA driver was causing serious problems (see thread #2107969). Ever since the system can't be unlocked after the lid was closed. When I reopen the lid I have a black screen, a moving mouse cursor, the time of the lid closed top middle and a lock with the user name next to it top right. There is no way to unlock the system, the screen stays black no matter what key you press. With the NVIDIA driver a login screen used to pop up after the mouse was moved or a key was pressed.

How can I diagnose the error and possibly fix it?

---

### Post by -kg- on 2013-01-31
I've never experienced this under 12.04, since I disable screen locking.

Have you tried clicking on the lock or user name?  Did this bring up a text box?  Usually, your administrator's password is required to unlock the screen.

---

### Post by omeomi on 2013-01-31
Perhaps try erasing all the nvidia-* related stuff and then reinstalling the nouveau driver to make sure there is no old driver causing havoc.

---

### Post by DrScum on 2013-02-01
@KG yes, I did try that, the system begins working, the mouse freezes but there is no login option appearing. The screen stays black

@omeomi, as described in thread #2107969 I think I really did get rid of all NVIDIA driver stuff. Is there a way of diagnosing this  though?

---

