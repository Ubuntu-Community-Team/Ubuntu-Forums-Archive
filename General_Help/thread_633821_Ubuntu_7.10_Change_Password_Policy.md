---
title: "Ubuntu 7.10 Change Password Policy"
date: 2007-12-07
forum: General Help
---

### Post by tony8gj on 2007-12-07
How do I change the password policy in Ubuntu 7.10 to change min password length?

I want to create a limited user account that does not have a password or, remove the need for a password on a current limited user.

Thx.

---

### Post by OliW on 2007-12-12
*bump*

I'd quite like to know too. I changed from the 3-letter password I created at install and now I can't change back.

---

### Post by aysiu on 2007-12-12
Try this:
[HowTo: Create a Passwordless / Guest Login (Simple Method)](http://ubuntuforums.org/showthread.php?t=513820&highlight=passwordless)

---

### Post by OliW on 2008-01-10
Passwordless is helpful *but* it breaks the current keyring manager. I believe this has been fixed upstream and might be with us by Hardy (could already be there) but that's not an ideal situation. I need keyring access now, not in a few months time.

Ideally, I'd just have a short password so this is another bump for changing the password policy properly (no offence intended toward your guest guide).

---

### Post by OliW on 2008-01-10
Bwahahahahaa!

```
sudo passwd <username>
```

Seems to ignore policies. Fantastic.

---

### Post by Bob Morane on 2008-02-05
Mhhh, i tried passwd, but it didn't work. I want to keep a 5 letters long password i've been using for common login since Breezy, but i wasn't able to set it in the Users and Groups GUI. So i created a 6 letters long password, and then tried to change it with sudo passwd. The command was accepted, but when i tried to log in, it rejected my 5 letters password. I had to enter the 6 letters one.
It looks like passwd wasn't able to change the password.
Any help will be appreciated. If i have to change some PAM parameters by had i'd like to be sure i don't do anything stupid.

---

