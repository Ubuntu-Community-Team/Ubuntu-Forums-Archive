---
title: "Single user mode"
date: 2007-02-07
forum: General Help
---

### Post by stubble on 2007-02-07
I'm trying to rescue the box of a terminated employee. When I boot to 'recovery mode', it says "enter root password for maintenance", but Ubuntu has no root password.

Clearly I'm missing something simple. Can anyone help?

---

### Post by r4ik on 2007-02-07
try,
sudo passwd root

---

### Post by koenn on 2007-02-07
1- it could work with the user password, as with sudo - I'm not sure about that, and it doesn't help you unless you know that password

2-just FYI, it is possible to get a working root account + root password on a Ubuntu system, and password-protecting maintenance mode with root password is generally a good idea.

3- There's a number of ways to work around it. Easiest : Boot of a live CD, mount the hard disk that contains /etc (eg to /media/hda1), edit /media/hda1/etc/passwd and possibly /media/hda1/etc/shadow to remove root password. This gives you a root account with no password.
Then boot the system (recovery mode, root, no password), create a user account and add it to the group "admin".
That will be the user that can do sudo, should you need it.

---

### Post by stubble on 2007-02-07
Thanks for the replies. I should have beem more specific: I want to recover the user's account, but don't know the password.

So, why would the Ubuntu project go to the trouble of setting up a recovery mode in Grub that's impossible to access?

---

### Post by koenn on 2007-02-07
> So, why would the Ubuntu project go to the trouble of setting up a recovery mode in Grub that's impossible to access?
Ubuntu's default is to leave recovery mode open.
Some people decide to password-protect it because it allows root access to anyone who can reboot the computer and select an item in the grub menu. There are situations where this is not desirable.

> I want to recover the user's account, but don't know the password.
get root / sudo access the way i described. 
From there, you're the administrator. You can find the account for the previous user in /etc/passwd , and reset the password with
```
sudo passwd *username*
```

try it. It works. It has been done before (do a search in the forums or post questions if you get stuck)

---

### Post by stubble on 2007-02-07
Thanks. That explains the password prompt, my employee must have set a root password at some point. 

Okay, so rather than hunt a LiveCD, I used the method outlined [*here*](https://www.noah.org/wiki/index.php/Single_User_Mode) to boot to a root shell without a password:

```
kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root rw init=/bin/bash
```

I then reset the user's account password (and root's as well) and now I'm back in business.

Thanks for your help!

---

### Post by koenn on 2007-02-07
yep, there's a number of ways to get around it. 

Because i pointed you in the right direction, i feel obliged to tell you that, depending on the legislation of your country, there may be legal/privacy issues involved in gaining access to someone else's files, even in an employer-employee relationship. I know there are in Belgium.

---

