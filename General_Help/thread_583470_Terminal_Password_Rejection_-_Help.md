---
title: "Terminal Password Rejection - Help?"
date: 2007-10-20
forum: General Help
---

### Post by gemesis912 on 2007-10-20
Hi all, I am running a new install of Ubuntu 7.04 (Feisty Fawn) and have a major problem.

I run the command "su" and it asks me for my password, I type it in (I know its not supposed to display any characters) and after a moment it says:

su: Authentication failure
Sorry.

I am 100% sure i am typing in the right password.  I have changed it several times in the Ubuntu GUI and then entered it into the terminal for it to be rejected.

Does anyone have any idea what is going on?

---

### Post by thirddeep on 2007-10-20
"su" without any arguments asks for ROOT's password, not yours. "sudo" asks for YOUR password.  

There is no root password by default, so do this :
```
sudo passwd root
```

Warning, using root can be dangerous ! :-)

Thd.
p.s. Use "su -" so you load root's profile.

---

### Post by gemesis912 on 2007-10-20
Thank you so much, knowing that could have saved me a few grey hairs :)

---

