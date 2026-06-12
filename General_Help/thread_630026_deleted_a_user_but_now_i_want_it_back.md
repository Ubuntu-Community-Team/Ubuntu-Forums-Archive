---
title: "deleted a user but now i want it back"
date: 2007-12-02
forum: General Help
---

### Post by rob1101 on 2007-12-02
well i deleted a user and their home directory (obviously don't care about the files) but i would like to make a new user using the same name as the old user but gutsy won't let me. every time i try to add the user it just simply does nothing.

---

### Post by lsmobrian on 2007-12-02
Did you use the graphical tool or command line (deluser or userdel) to delete the user?

---

### Post by rob1101 on 2007-12-02
i used the gui to remove the user and the command line to remove the users home folder

---

### Post by lsmobrian on 2007-12-02
wow, thats a weird one, i was playing around with my test user and pretty much got the same thing

I removed the user with users-admin  added the user back, logged out and couldnt login with recreated user... when i logged back in with regular user, recreated user was missing from users-admin.

so i tried the command utilities, they didnt work either

# adduser phil phil
adduser: The user `phil' does not exist.


How do i get an error about an user not existing when im adding that user???

---

### Post by rob1101 on 2007-12-02
yea its got me scratching my head.

---

### Post by lsmobrian on 2007-12-02
If there is a group with the same name as your missing user, delete that group then retry adding user

---

### Post by rob1101 on 2007-12-04
that go it thanks

---

