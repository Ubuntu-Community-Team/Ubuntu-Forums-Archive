---
title: "any way enable new user account"
date: 2014-03-30
forum: General Help
---

### Post by elim-qiu on 2014-03-30
It's ubuntu 13.10.

I used system setting to add a new user account but cannot enable it. Any way enable a new user account, say with shell and sudo? Thansk!

---

### Post by efflandt on 2014-03-30
See "man adduser". You will need to use sudo for adduser command (so it does that as root).

---

### Post by deadflowr on 2014-03-30
Where are you getting stuck at in system settings?

Is it at the add part?
Have you unlocked the settings page? (click the lock in the corner)

Or is the added account still coming up as disabled.(You need to click on password and give the new account a password)


Unfortunately, I find the password field for newer versions of Ubuntu's system setting user accounts thingy, to be rude, as it wants longer and more complex passwords, and it still tells you it's weak. the sudo/shell way only need a simple password and doesn't put you down.
me rants.

---

### Post by edcompsci on 2014-04-06
I have found that the kuser program works great.

[code]
sudo apt-get install kuser
[/code

---

