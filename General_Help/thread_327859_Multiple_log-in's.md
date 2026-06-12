---
title: "Multiple log-in's"
date: 2006-12-29
forum: General Help
---

### Post by gobuntu on 2006-12-29
Seems to me that one could via terminals log-in as more than one user.

However, after initial log-in, opening a second terminal and executing the login command, one gets the request to use the login from the lowest level "sh" (shell).

Have used briefly Linux ages ago, and just coming back.

Any info?

Thanks.

---

### Post by ciscosurfer on 2006-12-29
> **gobuntu said:**
> Seems to me that one could via terminals log-in as more than one user.

However, after initial log-in, opening a second terminal and executing the login command, one gets the request to use the login from the lowest level "sh" (shell).

Have used briefly Linux ages ago, and just coming back.

Any info?

Thanks.From a Terminal (shell), you can switch users by issuing the switch user command (su), followed by the user's name.  For example, to switch to user happy, enter in```
su - happy
```and then enter in that user's password (have that person issue if of course, or you can if you're an admin and know the password.  To exit back to the current user, issue```
exit
```You can also switch users by hitting your logout button in the upper-right corner and choosing switch user.

Hope that helps a bit

---

### Post by gobuntu on 2006-12-29
Thanks, but am questioning about being logged-in concurrently in more than one terminal, each a different user, not switching users.

Is it possible in Ubuntu?

---

