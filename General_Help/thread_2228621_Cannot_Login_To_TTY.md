---
title: "Cannot Login To TTY"
date: 2014-06-08
forum: General Help
---

### Post by Bubblegut on 2014-06-08
I am trying to login to my tty to fix another issue with installing video drivers, but I get stuck on the login screen. When I enter my username, it asks for a password but it shows no characters when I type. The cursor blinks according to when I press keys but stays at the starting point. I assumed the characters were just blacked out but when I enter my password it says that the login is Incorrect. I guess my problem is divided into two issues,
1. Why are the characters not showing?
2. Why are my username and password not working?
Could it have something to do with a password change in the past?

---

### Post by deadflowr on 2014-06-08
The password field will be invisible.
Type the password as best you remember it.

Getting past that point, what method did you do/use to change the password in the past?

As well, make sure the username is correct, including whether it has capital letters or not.

---

### Post by Bubblegut on 2014-06-08
I went to System Setting > User Accounts then unlocked my root account and changed the password. It should also be noted that when I first installed Linux I was having privilege issues and I changed the Account Type on my root account. 

EDIT:

I changed my group in Advanced User Settings. My shell is /bin/bash and I do not have a Main group.

---

### Post by deadflowr on 2014-06-08
Ubuntu's root account is locked, so it doesn't show in User Accounts.
Admin is the one your user would have been set to at installation time.

That said, it doesn't explain why the password fails.:(

Perhaps a password reset is in order
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Hope that helps, if it can.

---

### Post by Bubblegut on 2014-06-08
While in my User Settings I noticed that my actual username was different from the one I am able to change. I can now access my tty. Thankyou for your help, anyway! :P

---

### Post by deadflowr on 2014-06-08
> **Bubblegut said:**
> While in my User Settings I noticed that my actual username was different from the one I am able to change. I can now access my tty. Thankyou for your help, anyway! :P

It happens, sometimes more often then you'd think.
Unrelated, I once was trying to log into a system and it wouldn't except my password.
Turns out I, for some odd reason, kept pushing the spacebar, even though the password had no spaces.
(I took me about 5 tries before I settled down and slowly typed out the password, which I then realized my error)

Anyway, glad that's solved.

---

