---
title: "Upgrade from 21.04 to 21.10 Ubuntu Mate  can't select user account"
date: 2021-11-17
forum: General Help
---

### Post by SciGuy1872 on 2021-11-17
Hi.  Like the title states,  after using Update Manager to upgrade Ubuntu Mate,  the login screen doesn't allow me to choose a profile-- the only thing I can do is log in as a guest.

---

### Post by MAFoElffen on 2021-11-18
Can you get to a grub boot menu (pressing the left shift key repeatedly while booting)?

If so, go to the rescue boot option... Mount filesystem with networking. Root prompt...
```

apt install -f
dpkg --configure -a

```
And see if that corrects the update errors...

If that does not work, then you could always use that way in, to create another admin user to get in, create new users with that user, and copy over the old home directories to the new users.

---

### Post by SciGuy1872 on 2021-11-18
Hi.  The screen when starting UM has the black bar that has "Log In" written in it, and an arrow pointing right at the other end.   There is no way to select a drop- down entry where I could select my account. When I click the black bar, I am logged on as guest. Should I try to create other account, like you said, or is there maybe something else to try so that I can select an account to log into, instead of being forced to use a guest account? What are the two commands at the root prompt when in recover to tell the machine to create a profile, then create a password?  Should I bother with these steps even though I can't select an account to log into?  Thanks.

---

