---
title: "can't login"
date: 2006-10-29
forum: General Help
---

### Post by anubix on 2006-10-29
I have been off the face of the earth for a while as far as updating my ubuntu, so i downloaded 67 some odd updates, installed, on the reboot i got some sort of error just before the power cycled off and on.  Now it appears to boot up fine, however when i input my (correct) user/pass and hit enter, i get the "busy" cursor for the mouse, and after 30 sec. of no hdd activity, it goes back to login screen (and asks for user/pass again).  its an infinite loop.
how can i fix this?
i have a paper due tomorrow i'm working on which is 25% of my total grade, and i can't get to it.
if ever there was a linux emergency i think this might qualify!

---

### Post by .t. on 2006-10-29
Press "Ctrl+Alt+F1". Log in there. Post the output of ~/.xsession-errors. Delete the ~/.gnome2/session file.

---

### Post by dbott67 on 2006-10-29
If .t.'s suggestion doesn't work, try one of these:

1. The problem could be a corrupt ~/.ICEauthority file:
[quote=David M. Carney]Personally, whenever I have problems logging into Gnome, the first
thing I do is go to a tty (ctrl-alt-f1) and move my ~/.ICEauthority to
another folder.

I then try to login again. So far, this had worked for me.

When you try to login again a new ~/.ICEauthority file will be generated.

The reason I move the file instead of just deleting it is for in case
this "fix" does not work. Better safe than sorry.[/quote]

-or-

2. Login as a different user.  If there is only one user, boot into failsafe mode (or terminal) & create new user.
```
sudo adduser newusername
```
Then, add the new user to the 'admin' group:
```
sudo adduser newusername admin
```

Try logging in as this new user.  If necessary, copy your data files from your old /home folder (you may have to chown & chmod them first).

-Dave

---

