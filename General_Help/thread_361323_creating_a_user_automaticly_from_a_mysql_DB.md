---
title: "creating a user automaticly from a mysql DB"
date: 2007-02-14
forum: General Help
---

### Post by patty522 on 2007-02-14
i didn't know where to put this topic so i put here.

right i have a signup.php which a user puts the username, password, email, name that they would like. then that data is then put in to a mysql database. 

thing i was wondering about is it possible to have something that automatically create a computer user with that data that the person put in signup.php.

cheers all

---

### Post by digilink on 2007-02-14
The only way I can think of to do this would be to create a shell script that will pull the user data from the table and then create an account user adduser. There may be some prebuilt stuff out there already so you don't have to re-invent the wheel lol. (I'm guilty of that with a lot of things)

---

