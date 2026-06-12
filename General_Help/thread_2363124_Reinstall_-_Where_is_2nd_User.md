---
title: "Reinstall - Where is 2nd User?"
date: 2017-06-06
forum: General Help
---

### Post by Quarkrad on 2017-06-06
ruuning 16.04.   I've just done a re-install on a system with separate home partition.  I made sure the os partition was formatted but not the home partition.  All is OK in that I'm back to my Desktop but how do I get my 2nd user back?   I can see the 2nd user via the file manager but before, where I got an option what user to boot to, now I go straight to my own Desktop.  If I log out there is not an option to log into the other users environment.  2nd user is the wife so any help appreciated as she is asking me to get onto her pc now!

---

### Post by sotiris2 on 2017-06-06
You have kept the user's files but you need to add the actual user account again. First check the uid that owns the existing folder by > ls -n /home

You will have a number in the third row, possibly 100X. That is your old users uid and how linux really checks which user is which (not by the username). 

Then do > sudo useradd -M -u uid username
where uid is the number you found before and username the old username.

then do 
> sudo usermod -d /home/username 

to set the correct home directory for the user.

---

### Post by Quarkrad on 2017-06-06
Thank your speedy response. I discovered you can also get the user back by going to Users & Group and creating a new user **and** using the existing/old user name and password.

---

