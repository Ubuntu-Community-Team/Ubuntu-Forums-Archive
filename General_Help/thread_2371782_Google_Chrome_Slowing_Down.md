---
title: "Google Chrome Slowing Down"
date: 2017-09-18
forum: General Help
---

### Post by rolfUser on 2017-09-18
I remember my first distro being ubuntu 12.04 and Google Chrome would open up and I would have no problems. When I upgraded to 14.04, I noticed a dialog box open up every time I opened Chrome. 
Recently, I upgraded to 17.04 and Chrome had that same dialog box open on startup six times!
The dialog box does not open six times all at once. Instead it opens one at a time after I click "cancel". After the first 3 times, the home screen finally loads up and the dialog box appears until I hit "cancel" on the sixth dialog box. 

The dialog box reads, "Enter password to unlock your login keyring." It is a wide dialog box and there is a space to enter your password yet I never created an account.
Maybe you have seen this dialog box before. I didn't think much of it at first, and ignored it when it popped up six times, but after a few hours, I noticed that after opening a new tab, for instance, Chrome will start to freeze like it was running on a Windows OS.

I would like to know how to get it back and running again like it used to.

---

### Post by Autodave on 2017-09-18
I get the same thing. I just put the my password for Ubuntu in there and it is gone until I reboot.

---

### Post by untrustytahr on 2017-09-18
Usually people get that popup when they set "Auto logon" on their account.  Since they are logged in without putting in their password, the login keyring doesn't get unlocked.  The login keyring contains secrets like wifi and mail client passwords.  You can view them by opening seahorse (aka password and keys).

---

### Post by rolfUser on 2017-09-19
but why would that dialog box open six times when I open Chrome?
It crashes more often than ever now. I know there's a connection. I want to know how to find it and fix it if it is possible.

---

### Post by again? on 2017-09-19
> **rolfUser said:**
> but why would that dialog box open six times when I open Chrome?
It crashes more often than ever now. I know there's a connection. I want to know how to find it and fix it if it is possible.
There's no connection between that dialog box and your Chrome slowness/crashing.
I get the same dialog which needs to be closed several times if I don't use it to unlock the login keyring in the first instance.
If there was a connection, simple fix would be to turn off autologin as posted by untrustytahr.

---

