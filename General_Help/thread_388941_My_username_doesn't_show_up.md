---
title: "My username doesn't show up"
date: 2007-03-20
forum: General Help
---

### Post by FooBarWidget on 2007-03-20
I installed Ubuntu some time ago. I created a new user with the 'User and Groups' tool. The user was created successfully (I'm logged in to that account now), but the username doesn't show up in the 'Users and Groups' tool, nor does it show up in GDM. How can I fix this?

---

### Post by FooBarWidget on 2007-06-21
I found the solution. Edit /etc/login.defs, and set UID_MIN to my user's ID. My user ID is 500 but UID_MIN is set to 1000 by default.

---

