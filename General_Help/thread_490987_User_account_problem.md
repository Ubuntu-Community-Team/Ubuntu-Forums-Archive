---
title: "User account problem"
date: 2007-07-03
forum: General Help
---

### Post by kungphukenobi on 2007-07-03
Hi all, probably a bit of a noob question here.  
The main account i set up to run on my kubuntu installation will not currently log into KDE window manager, i have no idea why, the password is correct etc it just starts logging in then dumps me back onto the login screen.  This account also has run as su privelidges.  I managed to get around that though by just creating another user account from the cli and logged in using that...which worked great...kind of.

This new account lets me into KDE (must have been something funky in the other user account settings) but doesnt belong to any admin groups etc, so i cant run anything as su (wont let me click "administrator mode" button to change settings even though i know the root password)  and I cant log into x server as root.  

So i guess what I am after, is how do i change account permissions from the cli so that i can get su permissions on my account that I log into X with so i can change systems settings with the gui?  Does that make sense?

---

### Post by McNils on 2007-07-03
A think I got it ;)

Before you log in press Ctrl-Alt-F1
You log in with the user that cannot start KDE.
```
sudo usermod -a -G admin new_user
```

Try to start x.
```
startx
```
you might be able to see what the problem is...


Press Ctrl-Alt-F7 to be able to login with kdm.

---

### Post by bodhi.zazen on 2007-07-03
As an alternate, Ctrl-Alt-F1 to access the command line.

Log in as the user that can sudo and :```
sudo nano /etc/groups
```Add the new user to the end of the line :> adm:x:4:<user_1>,<user_2>

<user_1> = account with sudo powers
<user_2> = new account.

Second, if kdm is running, startx will not work .. so , logged in as the first user, the one you are having problems with, 

```
sudo /etc/init.d/kdm stop
startx
``` Post any error messages.

---

### Post by kungphukenobi on 2007-07-03
my thanks to you sirs! 
Mcnils, The "usermod-a -G admin user" was what i was looking for, now the new account i created will let me "run as su"  thanks muchly.

thanks bodhi.zazen , I didnt realise you could just edit a file for user priviledges, will probably use that again.  

Woo! i once again have power in the gui!

---

### Post by McNils on 2007-07-03
> Add the new user to the end of the line :
 [quote][noparse]adm:x:4:<user_1>,<user_2>[/noparse] [/QUOTE]

I think it is membership in the **admin** group that gives sudo privileges...

---

### Post by avik on 2007-07-03
> **bodhi.zazen said:**
> ```
sudo /etc/init.d/kdm stop
startx
```

Or you can do this in one step:

```
sudo /etc/init.d/kdm restart
```

---

