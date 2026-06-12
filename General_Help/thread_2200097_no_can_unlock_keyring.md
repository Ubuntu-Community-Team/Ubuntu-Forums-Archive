---
title: "no can unlock keyring"
date: 2014-01-17
forum: General Help
---

### Post by mayagrafix on 2014-01-17
I reset my login password via terminal passwd command and now this pops up every 5 minutes. 

[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/login_keyring_zps437f35d8.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/login_keyring_zps437f35d8.png.html)

How do I fix? don't remember using the password and keys before, and the panel is empty. Should I add a new account?

[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/Passwordampkeys_zps9f19904a.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/Passwordampkeys_zps9f19904a.png.html)

Thanx for ur great help, it is really appreciated.

---

### Post by Dave_L on 2014-01-17
Does this help?

[http://ubuntuforums.org/showthread.php?t=1615575&p=10084288#post10084288](http://ubuntuforums.org/showthread.php?t=1615575&p=10084288#post10084288)

---

### Post by mayagrafix on 2014-01-17
Thanks. Thread has useful info (Seahorse?) but in my case there is no _previous keyring password or Password tab_
> 
The fix is to change the password for login in seahorse:

To change the login password in seahorse press alt-F2 and type in: seahorse
**Go to the Passwords tab (the left tab)**
Right-click on Passwords: login
Select change password
Type in your old login password, then enter the new login password twice.

This should sync the passwords and solve your problem. If you only want to synchronize then use the same password for old and new

You need to do this also if a user changes his/her login password in the "about me" option of the admin menu.
here is screen grab of Seahorse:

[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/SeahorsePasswordKeyring_zpsfe77c369.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/SeahorsePasswordKeyring_zpsfe77c369.png.html)

Should I create a new Password and Keyring account?

---

### Post by Dave_L on 2014-01-17
Did you use the passwd command while logged in under your normal user account?

Try rebooting into recovery mode, dropping to a root shell and changing your password that way:

```
passwd USERNAME
```

Or this may work ("Alternatively"):

[http://ubuntuforums.org/showthread.php?t=1695764&p=10497521#post10497521](http://ubuntuforums.org/showthread.php?t=1695764&p=10497521#post10497521)

---

### Post by mayagrafix on 2014-01-17
Yesterday I changed password via control panel under normal user account but was unable to login afterwards with new password. Reboot into recovery mode >> root shell >>> passwd command and reset password from there.

Should I reset password **AGAIN**? either by recovery mode or in a terminal?

---

### Post by mayagrafix on 2014-01-17
> To reset everything my notes say "**Delete all the files in ~/.gnome2/keyrings**, logout, login, then start again"

In my case, the gnome2 folder is empty.

---

### Post by Dave_L on 2014-01-17
This is getting too confusing. I give up.

Hopefully someone else will be able to solve this for you.

---

### Post by stinkeye on 2014-01-17
> **mayagrafix said:**
> In my case, the gnome2 folder is empty.

In the seahorse view menu, check you have "By keyring" and "show any" ticked.
You should be able to right click on **Login** and change password.

**[SIZE=3]or[/SIZE]**

You could also do this but will loose passwords if any. UbuntuOne and google-chrome save passwords here.
UbuntuOne will create a new entry in the Login keyring when you run U1 and sign in again. 
Go to **~/.local/share/keyrings** and rename **login.keyring** to **login.keyring.OLD** 
A new login.keyring file should be created using your new password after you log out then back in.

---

### Post by mayagrafix on 2014-01-30
> **stinkeye said:**
> 
You could also do this but will loose passwords if any. UbuntuOne and google-chrome save passwords here.
UbuntuOne will create a new entry in the Login keyring when you run U1 and sign in again. 
Go to **~/.local/share/keyrings** and rename **login.keyring** to **login.keyring.OLD** 
A new login.keyring file should be created using your new password after you log out then back in.

The above seems to have done the trick. The other answers do not seem to apply to version 13.10, present Seahorse dialogue box different from given examples. Thanx everybody for all ur help!

---

