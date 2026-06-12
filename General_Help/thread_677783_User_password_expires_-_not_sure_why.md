---
title: "User password expires - not sure why"
date: 2008-01-25
forum: General Help
---

### Post by cmwilliams on 2008-01-25
Hello

I have a user on ubuntu server that for some reason seems to expire. it is the only user that this happens to and the person in question only logs on once a week

as soon as i use passwd to reset the password it works fine until the following week

this is the only user it happens to and is set up the same as all the other users

any one any ideas

cheers

---

### Post by tekreloaded on 2008-01-25
If you run the command:

sudo chage --expiredate -1 [USERNAME]

replacing [USERNAME] with the username of the user, this should turn off any password expiry settings on that user.

This can be run from the terminal and requires root access so make sure you are able to use sudo...

EDIT:

Alternatively you can just type:

sudo chage [USERNAME]

and set all of the values it asks you for to -1
 This is in fact probably a better idea.

---

### Post by cmwilliams on 2008-01-25
ok done that now

will see what happens next week

thanks for the reply

---

