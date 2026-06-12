---
title: "Undesirable Restart"
date: 2007-03-01
forum: General Help
---

### Post by larini on 2007-03-01
I have 2 users in my ubuntu.
I make login in user 1.
Then, I change to user 2 without logout user 1.

User 2 can restart computer with user 1 session active.

This is not desirable.

---

### Post by zvacet on 2007-03-02
Let´s say user1 is administrator(root),and user2 is not.You don´t want log in as root didn´t you.Go to System -> Administration -> Login Window
```
Security Tab -> Enable Automatic Login (Checked)
Now choose a user from the drop-down menu.
```
Choose non-root user.Most of the time you will work on comp as a common user without sudo privileges.When you need sudo privileges switch user.

---

### Post by Ramses de Norre on 2007-03-02
[This](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/) might interest you.

---

### Post by larini on 2007-03-02
Thanks, but I just want a simple thing. I share my computer with my wife. Some times I let computer doing some download, etc.. My with then comes and change to her user, make some thing and shutdown.. No message is displayed, nothing.. My work is loose.

I there is only one user logged in, no problem to him shutdown computer. But if there is more than one, only root could do it.

---

