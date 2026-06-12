---
title: "passwordless login/gdm"
date: 2007-01-09
forum: General Help
---

### Post by TheJackofClubs on 2007-01-09
my laptop is being passed around and im trying to make a guest user account on it so i dont have to keep logging in for people. im got [http://www.gnome-look.org/content/show.php?content=22926](http://www.gnome-look.org/content/show.php?content=22926) to use as my gdm login theme since it has a nice userlist. im trying to remove the guest account password for atleast the login screen. i followed several suggestions and nothings worked.

fist i tried```
passwd -d guest
```but it just made the account unable to login to without reseting the password.

next i tried editing /etc/passwd and removing the "x" near the guest account but that also made it impossible to log back into the guest account.

i did some google searching and edited /etc/pam.d/gdm adding the line```
auth    sufficient      pam_listfile.so sense=allow file=/etc/passwordless item=guest
```above```
@include common-auth
```and i could still login to guest but i had to use the password.

any ideas? thanks. :cool:

---

### Post by scrooge_74 on 2007-01-09
but give the guest account a password and tell it to people, you should not be having users without passwords is almost as having windowze in your laptop :D

---

### Post by Buck2348 on 2007-01-09
I'm not sure it can be this simple, but can't you go System -> Administration -> Login Window -> Security Tab -> Tick "Enable Automatic Login" and select the user from the drop-down.  This works for me as the (only) user--don't know about guest.

Buck

---

### Post by scrooge_74 on 2007-01-09
You can certainly try that

---

### Post by TheJackofClubs on 2007-01-09
oh i meant to say i didnt want to do automatic login since there are 4 other users besides guest on the laptop. i just wanted no password for the guest but its not a default account. and just fyi i am running windows in dual boot on the laptop for needed windows programs that wont work under wine and that windows account does have an unprivledged passwordless guest user. thanks for the reply ill keep looking. :)

---

