---
title: "Structure of Home folder for new User accounts"
date: 2008-04-01
forum: General Help
---

### Post by Last_resort_33 on 2008-04-01
I am attempting to create a sort of restricted system using Edubuntu. What I want to do is to have a group of settings that cannot be changed. What I want to do is to edit the way that a user's home folder is created when the user is created. 

Most importantly, I want the Desktop and .gconf folders to be links to root owned, write protected folders somewhere like /etc/usersettings.

Thus I can set peoples desktops and gnome settings myself, and the users will not be able to change them.

how feasible is this, and how do I set it so that it is set up automatically when I, or a low witted member of staff creates a new student user?

Hope this makes sense

---

### Post by rlcomstock3 on 2008-04-01
I would look into scripting a solution, any of the languages would work.  Python, ruby, perl, php, or even bash.  Pick one you know and create a "addStudent" script, have it make the account, then make the changes to the home directory.

---

