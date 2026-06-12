---
title: "Hardy User Passwords"
date: 2008-06-11
forum: General Help
---

### Post by grogger13 on 2008-06-11
I used to have 7.10 on my home desktop and all my family had a 5 letter password for there users.  I wanted it to be easy and the user password is not a big, just want my mom and sister to be able to get on the computer.  Now i did a fresh install of hardy and when i tried to add a user and put the same password my family knows it told me it was to short.  The one account i already have on the computer has a 5 letter password and it didn't say anything about that one.  I don't want them to have to remember a new password, even a little bit of change to something that was working fine is gonna be a pain in the neck.  How can i get there same password back.

-They dont have accounts on the computer yet since the install.

---

### Post by HalPomeranz on 2008-06-11
If you set the password with sudo, you will be able to set a short password.
So do "sudo passwd <username>", where you replace <username> with the user name of the account you want to set the password for.

---

