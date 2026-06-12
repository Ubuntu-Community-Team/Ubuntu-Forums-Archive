---
title: "ubuntu new user? plus another one..."
date: 2008-03-05
forum: General Help
---

### Post by corvettecraz92 on 2008-03-05
Okay, first things first: I installed ubuntu 7.04 with wubi, and everyting went fine. The only thing is, i forgot the username/PW i entered for it, and now i can't get into ubuntu. Help?

and also another thing: how do i get the wusb54g v4 drivers without having the internet on the machine in ubuntu?

thanks for the help in advance!

---

### Post by taurus on 2008-03-05
If you can boot into recovery mode from GRUB menu, you can see what your login name is from the output of this command.

```
ls -la /home
```
And one you know the your username, you can change the password with

```
passwd john
```
_Assuming_ john is your username.

Then, you can reboot with

```
shutdown -r now
```

---

### Post by corvettecraz92 on 2008-03-05
thanks! password succesfully reset...

And i solved my other problem! i am now posting from ubuntu 7.04! thanks guys!

---

