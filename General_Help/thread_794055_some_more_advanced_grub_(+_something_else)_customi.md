---
title: "some more advanced grub (+ something else?) customization"
date: 2008-05-14
forum: General Help
---

### Post by vexorian on 2008-05-14
Err, I've been thinking that the usual boot ubuntu, login in gdm process could be improved a little, and it is that if I go away of the computer during the boot time, there will be some little wasted time later as no one will place the password for a while.

I am usually the only user that can log in to ubuntu, other people do use the computer, but that's usually XP, some times though someone else will use ubuntu, so a partial solution involving it always logging me automatically would not work here.

What I was thinking is, add a special GRUB option to boot the kernel and log me in automatically, just make it (grub) request my password first if I pick that option.

Adding a password to one of grub's option is something I already know how to do, but how do I make grub able to tell gdm/something to log me in automatically?

---

### Post by meierfra. on 2008-05-14
You can   set the computer to lock in automatically but only  after a    delay. This will give other users time to lock in.

---

### Post by vexorian on 2008-05-14
I wouldn't really want to give other people access to my account without my password.

---

