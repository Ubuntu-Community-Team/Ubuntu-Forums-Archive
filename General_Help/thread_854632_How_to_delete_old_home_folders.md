---
title: "How to delete old home folders?"
date: 2008-07-09
forum: General Help
---

### Post by gothdc on 2008-07-09
As the question says, does anybody know how to do this? I have a lot used space because of this. Please Help. (ubuntu 8.04)

---

### Post by russo.mic on 2008-07-09
why do you have old home folders?  old users?  anyway,  you need to get rid of the old users in System ---> Administration ---> Users and Groups, highlite and delete.

I "think" that it will delete them then, but if not, type

rm -r /home/"oldusername" 

where oldusername is the old users name.  

BE CAREFUL, as when you exectue the -r command, you will be deleteing recursively, i.e. ALL FOLDERS AND SUBFOLDERS.  make sure you get your path correctly, and make sure there is nothing in the home folders you need.

Good luck!

Russo

---

