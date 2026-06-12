---
title: "Unable to login to Ubuntu"
date: 2007-01-13
forum: General Help
---

### Post by rashido on 2007-01-13
Hi all, need some help here..

Recently got Ubuntu 6.01 installed as dual boot on my laptop and all was fine until I 
changed the username.

Initially it was "rootuser" (created this user during installation) then I changed
it to "user" while logged on as "rootuser" 

Now, when I try to login using the username "user", I encounter this error:

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 664 permissions. User's $HOME directory must be owned by user and not writable by other users.

After I click on OK, I encounter another error message:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem. 

Is there any way that I can rename "user" back to "rootuser" so that I can login? Or any other fixes available via terminal? 

Please assist..

---

### Post by taurus on 2007-01-13
Boot into recovery mode from GRUB menu and change the ownership of all files to user.
```
chown user:user /home/rootuser
```

---

### Post by rashido on 2007-01-13
Thank you taurus! That resolved the problem. Able to login now. :)

---

### Post by taurus on 2007-01-13
You're welcome.

---

