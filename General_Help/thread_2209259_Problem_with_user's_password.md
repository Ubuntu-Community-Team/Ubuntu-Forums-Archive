---
title: "Problem with user's password"
date: 2014-03-04
forum: General Help
---

### Post by EL-FRIAKH_Zakarya on 2014-03-04
Hi every one, so I've had a lot of problems recently with ubuntu (13.10), all resulted in me formating my Ubuntu partition, after that I found myself facing a new problem: I couldn't log in to my session since apparently I kept entering a wrong password, after looking on the web I did this:
* booted on the recovery mode
* than chose root (from the options that were given to me)
* entered : mount -rw -o remount
* than changed my password (and I was given the message : password has been successfully change)
Yet my login screen kept giving me the message "wrong password", I really don't know why this is happening, and was hoping if anyone would have an answer for me

P.S. I noticed that on the terminal of the recovery mode, when typing: ls /home, the directory's name was different from the user's name, is that normal?
One last question: is it possible from the terminal of the recovery mode to create a new user, and delete the current one? (since that's the only solution I can think of)

That's all, thank you to every one who'd post any help!

---

### Post by phidia on 2014-03-04
To delete a user use the userdel command [see here]("http://manpages.ubuntu.com/manpages/lucid/man8/userdel.8.html") for more info.
The useradd command creates a new user to make that user an admin [see this guide]("http://ubuntuguide.org/wiki/Ubuntu_Saucy_User_Administration#User_Administration").

---

### Post by EL-FRIAKH_Zakarya on 2014-03-05
Hi thanks for replying phidia, will it still work from recovery mode?

---

### Post by buzzingrobot on 2014-03-05
"/home" is one directory. Individual user "home" drectories are subdirectories of /home. If two users -- UserOne and UserTwo -- are created, their "home" files will be "/home/UserOne" and "/home/UserTwo".

Both useradd and its alternative adduser will create a home directory using the name of the specified new user.

---

### Post by amish_otaku on 2014-03-05
When you're logging into single user mode normally you are logging in as root, or so I thought. Try logging into your computer as root with the password that you entered previously. You might as boot back into Single user mode and try to change the PW for your user account. If you did indeed login as root, then you won't actually be under the /home directory like you're thinking, but will instead be under the path of "/root"

---

