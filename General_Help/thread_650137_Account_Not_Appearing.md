---
title: "Account Not Appearing"
date: 2007-12-25
forum: General Help
---

### Post by sekinto on 2007-12-25
I created five accounts. One does not show up when using the user/groups utility, however there is a /home/(user) folder for them and they can log-in. How do I get the user to show up with the utility?

---

### Post by adam.tropics on 2007-12-25
Scroll down!!! Kidding.

In gconf-editor there is a setting for show all users under /apps/gnome-system-tools/users/show_all maybe try checking that?

edit:maybe not. You could always delete the user from the command line (since he/she isn't showing up in the gui) the recreate it from the gui, see if you get any more luck?
```

sudo userdel <username>
```

---

### Post by nick_h on 2007-12-26
The user admin utility will only show accounts where the user id > 1000 by default. (and root).

The showall option doesn't work - see [bug #124993](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/124993).

---

