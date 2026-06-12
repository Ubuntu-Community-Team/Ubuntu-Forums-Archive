---
title: "User with no password"
date: 2006-11-02
forum: General Help
---

### Post by markus_b on 2006-11-02
My four year old daughter is starting to use a spare laptop for some games. I'd like her to be able to log in without typing a password. But there are some other users on the machine, so autologin to her user does not work.
I've tried removing the password from /etc/shadow, modifying /etc/pam.d/common-password with no success.

How can I make this happen ?

Markus

P.S. I know this is not secure and accept the risk involved.

---

### Post by jsandys on 2006-11-02
But she has to type in her user name?  I know this isn't the answer you wanted but I would make her password the same as her user name and I would make both of these a single letter like the first letter of her name.

---

### Post by markus_b on 2006-11-02
No she does not have to type her name. If you use 'Happy Gnome with Browser' as you Login window preference than you get a list of users (with picture).
It is sufficient to click on the picture to select the user. Then you just enter the password, <Enter> in her case.

Markus

---

### Post by bigken on 2006-11-02
system/administration login window select the security tab and enable automatic login select user ;)

---

### Post by ehird on 2006-11-02
read his post again.

---

### Post by markus_b on 2006-11-02
This works very nicely, but not as I would like. When the computer boots, it will start my daughter's session automatically. I want it to stop and ask for a login, not to start a session automatically !
*Markus*

---

### Post by bigken on 2006-11-02
like one of the above said give her a single letter user name and password

---

### Post by skymt on 2006-11-02
Can't you just run "sudo passwd *username*" and enter a blank password?

---

### Post by markus_b on 2006-11-02
Yes, since I removed the min=4 parameter in the pam config file I can change the password to nothing. Unfortunately I can not log in to that account...
*Markus*

---

### Post by markus_b on 2006-11-02
Yup, a single letter password is my fallback plan. I'd like to find the 'real solution', though.

*Markus*

---

