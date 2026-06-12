---
title: "Recover Mode Password Reset black Screen"
date: 2014-06-23
forum: General Help
---

### Post by Michael_Amit on 2014-06-23
I apologize I am new to Linux. I have a computer at work that hasn't been used in a while and no one remembers the password. Instead of testing a password reset on that actual computer, I am using a netbook that has lubuntu installed to see if I can get a password reset to work. The problem I am having is that when I reset the password using Recovery mode it looks like everything goes perfect until I try to log into the account that I just changed the password. I try to log in, it looks like it takes the password but the screen goes black for a second then goes right back to the log in screen. No error it just looks like it it wants me to log in again. I tried new password three times same thing and when I try the old password it says invalid password.


These are the steps to reach where I am:

-I created a new user "test1" (encryption on home folder is checked) and set the password to "helloPa$$1"

-Logged in to verify the account is good

-Rebooted computer held shift and booted into "Recovery mode"

-selected "root" from menu

Ran the following because I was in read only

mount -o remount,rw /  

then ran:

passwd test1

changed the password to "byeP@ss2"

typed it in twice and was successfull

rebooted computer tried to log in with new password and screen goes black for a second then back to login. Tried old password and get incorrect password.

Any ideas?

---

### Post by Michael_Amit on 2014-06-23
So apparently while reading other blogs it's because I had "encryption" checked. Does anyone know how to get around this in case the computer I will be working on has encryption check?

---

### Post by pqwoerituytrueiwoq on 2014-06-23
encryption uses the password for the account in the algorithm, what would be the point of encryption if you could bypass it in 30 seconds?
If you don't care about the data you can delete it and make a empty user folder
If you need that users data you have to resort to a brute force method or guess that users password

Personally I don't use encryption, it has a performance impact and i like being able use use low end hardware and it feel like a race car, lol

---

### Post by Michael_Amit on 2014-06-23
That's a good enough answer for me! If the user did use encryption and forgot their password then I have done everything I can. The user doesn't know if he used it or not so I guess I'll try a password reset and go from there!

Thanks!

---

