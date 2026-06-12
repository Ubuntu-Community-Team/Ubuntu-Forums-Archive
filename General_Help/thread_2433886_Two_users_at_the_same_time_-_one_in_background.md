---
title: "Two users at the same time - one in background"
date: 2019-12-27
forum: General Help
---

### Post by UBUminJ on 2019-12-27
(Problem is solved)

When I am uploading large amounts of data to Google Drive, exactly at that moment my wife wants to check her email. 
When I logout, the upload is canceled and I have to restart the upload - situation Ubuntu 19.04.

Having two users logged-in at the same time was possible in 14.04 but I don't find it in 19.04.
What do I need to change in the setup that this is possible again?

---

### Post by spjackson on 2019-12-27
Instead of logging out, if you lock the screen, then a second user can login from the locked screen.

---

### Post by Dennis N on 2019-12-27
Is this what you are after?
> 
**Log out or switch users**

To let other users use your computer, you can either log out, or leave yourself logged in and just switch users. _If you switch users, all of your applications will continue running, and everything will be where you left it when you log back in_.

To Log Out or Switch User, click the system menu on the right side of the top bar, click your name and then choose the correct option.

The Log Out and Switch User entries _only_ appear in the menu if you have more than one user account on your system.

---

### Post by cmcanulty on 2019-12-27
I do it all the time with Remmina. The vnc type connection goes with whomever is logged in but the rdp option lets you log in without affecting the other logged in user. Of course I do it from another remote machine but I don't think that matters.

---

### Post by UBUminJ on 2019-12-28
@DennisN
> The Log Out and Switch User entries only appear in the menu if you have more than one user account on your system. 
I have two accounts, the administrator (my account) and a user account, but the switch user entry doesn't show up when clicking my name. This is why I asked.

@spjackson
That does the trick.

Also thankyou to @cmcanulty. That sounds advanced. :D 

I let it now with this because I am going to replace 19.04 with the next LTS (20.04) anyway. Let's see if this PC is still running then - a Dell Inspiron 530s from 2005?.

---

### Post by cmcanulty on 2019-12-28
It is simple once set up. If you want the whole explanation I would be happy to post it.

---

