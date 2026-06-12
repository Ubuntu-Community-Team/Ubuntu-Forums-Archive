---
title: "synaptic package manager error"
date: 2007-08-20
forum: General Help
---

### Post by charlieruss on 2007-08-20
after opening my package manager:


an error occured
the following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

so i went to the terminal, entered the given command, and it told me i needed superuser privilages.

I then followed the suggestions in a previous thread as follows:-

sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade

But after each line I am asked for a password and am unable to type anything except for pressing enter.  After entering all the commands the problem still exists.

---

### Post by Happy_Man on 2007-08-20
Yes, even though you can't see it, your computer knows you are typing. Simply put in your password (even though you can't see it), and press enter. It will work. 

For more info, see here: [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

