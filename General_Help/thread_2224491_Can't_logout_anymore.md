---
title: "Can't logout anymore"
date: 2014-05-16
forum: General Help
---

### Post by jmeeter on 2014-05-16
I have Ubuntu 14.04 installed as well as Xubuntu installed alongside. Last night I logged in to an Xubuntu session and all was well. Today, however, I seem to have lost the ability to use the logout function. Can someone help me out with some commands or something? Thanks!

Edit: I should note that my goal is to change sessions, not log out from this user.

---

### Post by Tristan_Williams on 2014-05-16
Try running the following command in a terminal:
```

xfce4-session-logout

```

---

### Post by ihendley on 2014-09-22
I have the same problem. The 'Log Out...' option in the panel menu with the power button icon gives me a "Are you sure you want to close all program and log out?" dialog which does nothing when I press "Log Out". 

I was able to use xfce4-session-logout from the command line before, but something has changed and I now get the following error:

```

xfce4-session: Unable to contact D-Bus session bus (Unable to autolaunch a dbus-daemon without a $DISPLAY for X11).

```

I am using xubuntu-desktop installed on top of Ubuntu.

---

