---
title: "I cant get Ubuntu 7.10 installed"
date: 2007-11-24
forum: General Help
---

### Post by Millerchamp on 2007-11-24
I have a Ubuntu ios already but im not sure what version it is and i dont know if i can update it to 7.10. Can any one help me?

---

### Post by Kavjik on 2007-11-24
Run: "update-manager -d"

If it tells that 8.04 is available, then do nothing.
If it tells something else, then tell what is says.

---

### Post by gepatino on 2007-11-24
One way to know wich version are you running, is reading the file /etc/apt/sources.list, where the repositories are defined.

You will find several comments and lines similar to this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **gutsy** main restrictef

From this line you could tell that I'm using Gutsy (7.10), 

In order to upgrade to the latest version (7.10, gutsy), you should have installed version 7.04 (feisty)

If this is the case, open the update manager, mark all available updates for your system, reboot if necesary, etc.

After getting feisty upgraded to the latest packages, open again the update manager and you'll se a button at the top to Upgrade to version 7.10.

Click on it, follow the instrucions, and be patient :)


If you have an older version (6.10 or less) you would need to upgrade to each consecutive release... in this case, I would suggest you to reinstall with a Gutsy LiveCD.


PS: Ubuntu version numbers means year.month, this could be usefull when guessing which release are you using if you know when was it installed ;)

---

### Post by Millerchamp on 2007-11-24
Okay, I go to the update manager and I go to install all updates and this comes up "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." What does this mean? And any thing i do with the update manager that code above comes up, it's like the update manager doesn't work

---

### Post by gepatino on 2007-11-24
That error could mean that some previos update didn't finished as espected... maybe it was forced to quit before ending.

try running 'sudo dpkg --configure -a' in a terminal, and then try again.

---

### Post by Millerchamp on 2007-11-24
Okay, I entered that command 'sudo dpkg --configure -a' and it said need a password but it wont let me type any thing to put the password in?!?!?!

---

### Post by Millerchamp on 2007-11-24
Does any one know what's wrong and why I can't update my Ubuntu to the newest and latest version 7.10? (I don't know the version of Ubuntu i have right now)

---

### Post by gepatino on 2007-11-24
When you are asked for a password, insert your user password. While typing you won't see the characters you tike, for security reasons.

---

### Post by Millerchamp on 2007-11-24
Ok i got 7.10 installed thank you for all the help guys

---

