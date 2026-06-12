---
title: "My user account has no group name!"
date: 2013-07-18
forum: General Help
---

### Post by quickk on 2013-07-18
Hi everyone, 

   I messed up my user name when I installed kubuntu on my laptop.   I then created a second user with the correct user name spelling and deleted the first.   The "problem" is that now this second user's group has no name!

For example, if I do ```
ls -l
``` in my home folder the permissions show that all the files belong to the user "myusername" and to the group "1001".   This is strange since usually, the group will be the same as my user name.   When I try to change the group name via the kde User Management gui, it doesn't let me modify anything.    

I also tried using groupmod:
```
sudo groupmod -n amorris 1001
groupmod: group '1001' does not exist

```

How can I change the group name if it doesn't have a name to start off with?

---

### Post by efflandt on 2013-07-18
How did you create that 2nd user, with a gui or from a terminal.  Note that **adduser** is preferred over **useradd** (read man pages for those commands), because adduser sets things up more completely, whereas, useradd is more primitive and assumes that you know how to set anything else required.

One way to add the user's group is to edit /etc/group and add: **amorris:x:1001:**

The official way to do that is with **sudo vipw /etc/group**, but if you are really the only user you could do it with **sudo nano /etc/group**

To add a user to other groups the /etc/group entries are a comma separated list (example from Raspberry Pi running a version of Debian):

**audio:x:29:pi,pulse,efflandt**

---

