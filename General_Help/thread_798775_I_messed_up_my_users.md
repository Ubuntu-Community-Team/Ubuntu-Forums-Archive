---
title: "I messed up my users"
date: 2008-05-18
forum: General Help
---

### Post by Dracs. on 2008-05-18
I was trying to change my user passwords to have a fairly easy password for my user but a harder one for root. I changed the passwords around, If I enter "sudo su" into terminal I get this when entering my user password "Sorry, user dracs is not allowed to execute '/bin/su' as root on Zeriph." I have tried to give change the settings back, but it's all greyed out. Anybody know what the hell I did wrong?

---

### Post by ibuclaw on 2008-05-18
In your next post, can you tell us the steps you took to change the passwords (excluding the actual passwords you entered, obviously :D).

Regards
Iain

---

### Post by Dracs. on 2008-05-19
> **tinivole said:**
> In your next post, can you tell us the steps you took to change the passwords (excluding the actual passwords you entered, obviously :D).

Regards
Iain

I went to System>Admin>Users and Groups. I went to my user and changed the password there. Then on the user privilege tab I unticked "Administer the System". I then went in to the root user, changed the password and I believe I just ticked everything under user privileges.

---

### Post by angry_johnnie on 2008-05-19
Then it looks like you set a password for root, didn't you?  If that is the case, when you type sudo su, do not enter your password, but rather root's password.

su (switch user) points to root, if not told otherwise.

However... you deselected the 'administer the system' option for yourself.

I don't think you'll be allowed to sudo anything...

You might want to change that back.

---

### Post by Dracs. on 2008-05-19
> **angry_johnnie said:**
> Then it looks like you set a password for root, didn't you?  If that is the case, when you type sudo su, do not enter your password, but rather root's password.

su (switch user) points to root, if not told otherwise.

However... you deselected the 'administer the system' option for yourself.

I don't think you'll be allowed to sudo anything...

You might want to change that back.

I have tried to change it back but pretty much everything is greyed out for me. I can't retick the "administer the system" and I can't look at the root user from the user settings box.

Also when I do type in "sudo su" It asks for the password for my account not root.

---

### Post by aysiu on 2008-05-19
Type ```
su
``` and this will switch you to the root user (enter root's password, not the user one). Then ```
adduser *username* admin
``` where *username* is your actual username.

---

### Post by angry_johnnie on 2008-05-19
Ok, try this in terminal.

```
su
```
**without** sudo!

enter root's password

then enter this line:

```
useradd -G admin your-user-name
```

and enter.

It should add you back to the administrator group.

Whoops!  Aysiu came in faster... and probably more accurately :-)

---

### Post by Dracs. on 2008-05-19
> **aysiu said:**
> Type ```
su
``` and this will switch you to the root user (enter root's password, not the user one). Then ```
adduser *username* admin
``` where *username* is your actual username.

Thanks Aysiu and everyone else, that worked perfectly. Now I won't try anything myself, but is there anyway to do what I originally wanted. To have a easy login password and a harder password for root stuff.

---

### Post by aysiu on 2008-05-19
Apparently, according to [what used to be on the Wiki](http://ubuntuforums.org/showpost.php?p=1050142&postcount=4), you edit the /etc/sudoers file using the command ```
sudo visudo
``` and then add the word *rootpw* to the line that starts with the word *Defaults*

---

### Post by stevelikesit on 2008-07-13
Greetings, As a NB, I did the same thing. I unchecked admin privilege and now I can't restore my admin privilege. I have no root p/word. I have one other user account with out admin. I've tried to enable that account to admin but it won't work. I've tried terminal with the suggestions in the forum but with no success. Just when I was beginning to like Linux. I'm I screwed?

---

### Post by mnglfiddle on 2008-07-14
> **stevelikesit said:**
> Greetings, As a NB, I did the same thing. I unchecked admin privilege and now I can't restore my admin privilege. I have no root p/word. I have one other user account with out admin. I've tried to enable that account to admin but it won't work. I've tried terminal with the suggestions in the forum but with no success. Just when I was beginning to like Linux. I'm I screwed?
No, you're not. Boot up with the Ubuntu install CD and running that, open up a terminal and type 'sudo nautilus'. Then go to your hard drive and find the /etc/group file. Open that and scroll down the 'admin' line, and you should see something like "admin = root". Simply type, with no spaces, ",*your-user-name*. Again, make sure there are no spaces between "root" and the comma and your user name. Then save, and reboot. You should then have root access again.

I just did the same thing last week and figured this out.

Matthew

---

