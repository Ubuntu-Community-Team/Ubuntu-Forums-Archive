---
title: "Ubuntu 7.10 Login Problem"
date: 2008-03-13
forum: General Help
---

### Post by Gambylad on 2008-03-13
hI 

Can anyone help with my login problem .
new install but been able to access no problem but on last boot I get message username or password incorrect case but it is not and I cant access my system

Help

---

### Post by taurus on 2008-03-13
Boot your machine into recovery mode from GRUB menu.  Then at the prompt, check to make sure your have your login name, username, right.

```
ls -la /home
```
Assuming your login name is john, change the password to something that you can remember with

```
passwd john
```
Now, reboot and see if you can log in as john with the new password.

```
shutdown -r now
```

---

### Post by Gambylad on 2008-03-13
Hii
thanks for help but as a new user how do I access grub on boot up

---

### Post by taurus on 2008-03-13
If you don't see the GRUB menu when you boot up, press Esc key to display it.  From there, the recovery mode is the second option, usually.  You have 3 seconds to press it or it will automatically boot into Ubuntu.

---

### Post by Gambylad on 2008-03-13
cheers i will give that a try

---

