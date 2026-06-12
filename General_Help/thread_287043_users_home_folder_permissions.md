---
title: "users home folder permissions"
date: 2006-10-28
forum: General Help
---

### Post by lemonsCC on 2006-10-28
I have the home folder on a separate partition.  I just did a fresh install and 2 of the 4 users on this computer work "flawlessly,"  However the other two give me errors about $HOME/.dmrc and something about 644.  Then it goes to another screen and says you were logged in for less than 10 seconds...then back to the log in screen.

Please help :confused:

---

### Post by DaveBorealis on 2006-10-28
> **lemonsCC said:**
> However the other two give me errors about $HOME/.dmrc and something about 644.

Not sure what's up, but 'ls -la /home/<user>/.dmrc' on my machine looks like:
```
-rw------- 1 <user> <user> 26 2006-10-19 13:30 .dmrc
```
If yours isn't '-rw-------', then try
```
sudo chmod 600 /home/<user>/.dmrc
```
And see if that doesn't make the login happy.

If not, then maybe the .dmrc file is screwed up and you need to copy over it.  Again, on my system the .dmrc contains a single line:
```
Session=default
```

---

### Post by bsussman on 2006-10-28
for the .dmrc file to have correct perms:

```
sudo chmod 644 ~whoever/.dmrc
```

---

### Post by galileon on 2006-10-28
looks like a permissions problem to me,
from an account which works, 
open a terminal and type

sudo chown username:username /home/username/ -R

replacing username with..well the username...

hope this works...

edit: provided the user you are logged in as is in admin group, ie can use sudo...

---

### Post by bsussman on 2006-10-28
> **galileon said:**
> looks like a permissions problem to me,
from an account which works, 
open a terminal and type

sudo chown username:username /home/username/ -R

replacing username with..well the username...

hope this works...

edit: provided the user you are logged in as is in admin group, ie can use sudo...

chown won't have an effect on permissions - chmod is the permissions command...

---

### Post by lemonsCC on 2006-10-28
> **bsussman said:**
> for the .dmrc file to have correct perms:

```
sudo chmod 644 ~whoever/.dmrc
```

tying it now.

Thanks for the replies! :KS

---

### Post by lemonsCC on 2006-10-28
No luck.

---

### Post by meng on 2006-10-28
It may be necessary to do both chown (to change owner) AND chmod (to change permissions). You can login with the same username IF you choose a failsafe terminal session rather than GNOME/KDE.

Alternatively, sudo rm ~whoever/.dmrc will work also (by deleting the file altogether).

(I know, I came across exactly the same problem yesterday and solve it that way.)

---

### Post by graigsmith on 2006-10-28
before you change ANY permissions make sure the ownership is correct.

edit, if you notice someone else owns it or no one owns it.

you will have to do a ```
sudo chown -R user:user /home/user
```

if you put the correct user name here, in place of user, it should fix the ownership.  this sometimes happens if you recreate users in a different order than you did the last time.  They get a different user number. and it causes problems.

---

### Post by lemonsCC on 2006-10-28
maybe this is the problem:

```
chris@Campbell:~$ sudo ls -la /home/pam/.dmrc
-rw-r--r-- 1 tim users 26 2006-10-06 18:10 /home/pam/.dmrc
chris@Campbell:~$ 

```

the permissions for user "pam"  say that time is the owner
the reverse is also true.  How could this happen?  How can it be fixed?

EDIT:  trying chown now

---

### Post by meng on 2006-10-28
If you didn't enter the 4 users in the same order they were entered originally, they will have different user IDs, e.g.
1001, 1002, 1003, 1004 vs 1001, 1003, 1002, 1004
This is why you have 2 users transposed.

---

### Post by lemonsCC on 2006-10-28
> **meng said:**
> If you didn't enter the 4 users in the same order they were entered originally, they will have different user IDs, e.g.
1001, 1002, 1003, 1004 vs 1001, 1003, 1002, 1004
This is why you have 2 users transposed.

OH!  DUH.  I completely forgot about user IDs.  Thanks for the explanation.  I always like to know "why?"

---

### Post by lemonsCC on 2006-10-28
Ok the first problem is solved.  It now gives the second error which i breifly described in the first post.

i can't copy/paste the error, but it says something along the lines of
```
cannot set 0700.../home/tim/.gnome2_private/
```

---

### Post by lemonsCC on 2006-10-28
Ok although I chown-ed the .dmrc file and the home folder, it didn't seem to chown the contained files and folders, which is why I am getting the above error.  How can I chown the users home folder and have all enclosed files chown-ed as well?

---

### Post by meng on 2006-10-28
chown -R
should change owners recursively

---

### Post by lemonsCC on 2006-10-28
thanks

---

### Post by charles nicholls on 2006-11-16
this one had me foxed to, but fixed the prob the simple way (simple is as simple does) install nautilus scripts, browsed to my user folder (dad) right click and selected root-nautilus-here  changed the permissions to owner-folder access
create and delete files. file access .....

group and others to folder access .Access files. file access ....
restarted and its back to normal, probably an arse about way to do it but
whatever:-D

---

