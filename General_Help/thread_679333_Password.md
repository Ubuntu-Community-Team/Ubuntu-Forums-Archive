---
title: "Password"
date: 2008-01-26
forum: General Help
---

### Post by gamckinney on 2008-01-26
I just bought a used computer with Ubuntu installed on it from a recycle station. I have found that I need a password to awaken the computer after it has gone in standby mode and to access "Users and Groups". I don't know what the password is. What can I do to remedy this?

---

### Post by taurus on 2008-01-26
Boot into recovery mode from GRUB menu and change the password of that account.  _Assuming_ the username is john, run

```
passwd john
```
You have to type the new password in twice.  Then, you can reboot with

```
shutdown -r now
```
Now, you should be able to log in as john with the new password.  If you want to use sudo, you need to belong to group admin so open a terminal and post the output of this command here.

```
id
```
p.s.  Which release are you using anyway?

---

### Post by gamckinney on 2008-01-26
Thanks for the reply but how do I boot into recovery mode and where do I find the "Grub" menu? I'm running 7.10

---

### Post by nbayiha on 2008-01-27
When you start u computer , after the loading page u get to a page where u are suppose to choose between different OS,
This is a grub loader.

To first line should be ubuntu normal booting and the second line should be the booting line in recovery mode.
To boot there just go the line and press enter :p.

And by the way i really doubt that what Taurus told you will work because actually you need to edit first the recovery mode.

Anyway try first his method if i doesn't work reply and i will try to help you.

---

### Post by gamckinney on 2008-01-27
When I turn the computer on it boots right in Ubuntu. It doesn't give me any options. So far as I know Ubuntu is the only OS on the machine. Everything works fine. I just can't perform any of the administration functions.

---

### Post by taurus on 2008-01-27
If you don't see a menu when you turn on your computer, press Esc key to bring it up.  Remember, you have 3 seconds to press Esc or it will boot into ubuntu.

---

### Post by gamckinney on 2008-01-27
That did the trick. My thanks to both of you for your help.

---

