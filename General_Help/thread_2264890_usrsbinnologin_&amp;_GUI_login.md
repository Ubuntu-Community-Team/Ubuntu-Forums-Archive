---
title: "/usr/sbin/nologin &amp; GUI login"
date: 2015-02-10
forum: General Help
---

### Post by balia on 2015-02-10
I've an account with /usr/bin/nologin as the login shell.
If I try to su to that account, I get the message
 "This account is currently not available" 
as expected...

However I can still login to that account from the GUI screen and the account even gets its own desktop.
Removing the account home folder prevents GUI login; but this creates another set of problems such as applications failing to launch.

How do I prevent GUI login for this account?

Thank you

---

### Post by steeldriver on 2015-02-11
Hmm... I wonder if it's related to the change from [UserAccounts] to [UserList] mentioned here --> [How do I hide a particular user from the LightDM login screen?]("http://askubuntu.com/a/97248/178692") [askubuntu]

---

### Post by balia on 2015-02-11
Modifying  /etc/lightdm/users.conf doesn't resolve it ...
Adding the account name to the line "hidden-users=" makes no difference and the account is still able to login in the GUI.
In my case, I hide all the user names from the login GUI so all users have to type both their user name and password.
The account with the "/usr/sbin/nologin" shell can still login by inputing the right credentials.

---

