---
title: "Can't log into GNOME or access /home"
date: 2006-10-06
forum: General Help
---

### Post by hygraed on 2006-10-06
For some reason, I cannot log into GNOME any more, or access my /home folder. I am presented with the fancy-pants login screen, and if I try to log into GNOME (failsafe or no) I get this:

> Your home directory is listed as:
'/home/marshall'
but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session.


If I click "No" it dumps me back at the login screen. If I click "Yes" it pops up another message saying

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.


When I click "OK" the login screen disappears, it makes like it's going to login and then it gives me a message saying

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.


That box has an option to view my ~/.xsession-errors file, which reads as follows (this is not the whole thing but only the pertinent part):

```
(gnome-session:4802): libgnome vfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory `/home/marshall/.gnome2': Permission denied
```

Interestingly, even when I go into a terminal and use fakeroot to try to access my /home folder, it says "permission denied."

Oh God I really did it this time. Can anyone tell me how to fix this, or, failing that, save my /home/marshall folder?

---

### Post by astoltz on 2006-10-06
This looks like your home directory got it's permissions mixed up somehow.  You'll have to boot to single user mode - from Grub at boot-time not from the fancy-pants login screen.  Single user mode will leave you at a command prompt.  From there you should be able to fix the permission / ownership problems with your normal home directory.

---

