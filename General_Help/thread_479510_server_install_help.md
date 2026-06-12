---
title: "server install help"
date: 2007-06-20
forum: General Help
---

### Post by Tucatts on 2007-06-20
I have installed both the 6.06 and the 7.04 server versions ( tried both) and I get the same problem with both. I am probably doing something really stupid but can't decide, lol. Anyway, the install seems to go fine but I can never log in. I am asked during the install for a host name and a user account name and a user name for the account. Ok no problem I put that in as well as the password it asks me to type in. So far so good until I reboot for the first time and after it goes through the boot up process it asks me to log in using the host name I had entered. I enter it and then the password and then get "login failed" I have tried this with the hostname, the user account name etc. No go. Both versions do this so what the heck am I doing to cause this?
Thanks,
Tucatts.

---

### Post by phantomdata on 2007-06-20
You'll be logging in with the username and password.  The hostname is irrelevant for login credential purposes.

What's happening to you seems really strange, but I have two quick suggestions.  Number one, check your caps lock and numlock.  I know it sounds stupid, but I've been known to screw up passwords in this fashion myself.  Number two, double check that the keyboard is functioning.  I know that Dell PE 1850's have an issue where a USB keyboard double-types from time to time.

Also, have you tried totally wiping the hard disk and starting from scratch?  Perhaps there's some leftover scraps from a prior install that weren't getting wiped out by these installations?

---

### Post by dreadlord_chris on 2007-06-20
> **Tucatts said:**
> I have installed both the 6.06 and the 7.04 server versions ( tried both) and I get the same problem with both. I am probably doing something really stupid but can't decide, lol. Anyway, the install seems to go fine but I can never log in. I am asked during the install for a host name and a user account name and a user name for the account. Ok no problem I put that in as well as the password it asks me to type in. So far so good until I reboot for the first time and after it goes through the boot up process it asks me to log in using the host name I had entered. I enter it and then the password and then get "login failed" I have tried this with the hostname, the user account name etc. No go. Both versions do this so what the heck am I doing to cause this?
Thanks,
Tucatts.

Your log in is the **user name** & password - not the host name or user account name. There should be **no** spaces in the user name - and both name & password **are case sensitive**

---

