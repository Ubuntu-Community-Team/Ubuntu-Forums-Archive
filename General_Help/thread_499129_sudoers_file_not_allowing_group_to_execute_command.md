---
title: "sudoers file not allowing group to execute command"
date: 2007-07-12
forum: General Help
---

### Post by thikrat on 2007-07-12
Hello,

I want firestarter to be automatic on startup for any user using the system.  I understand that i need to use visudo to edit the sudoers file and i did.  I want anyone in the users group to have this launch automatically on start without typing in a password.

so i added this line to the sudoers and saved it...

%users ALL= NOPASSWD: /usr/sbin/firestarter

I then typed

sudo -K

so the new settings would be read in... i then tried starting firestarter with sudo, and was promrped for a password.  i went back in and changed the "users" to my username.  did the "sudo -K" again and tried launching firestarter.  this time it worked just fine.  I tried this three times just to confirm.  Can anyone give any tups? this seems very basic!  I also confirmed that my username is part of the users group just to be extra careful.

thanks

---

### Post by kerry_s on 2007-07-12
```
%firestarter ALL=(root) NOPASSWD: /usr/sbin/firestarter

sudo addgroup firestarter

gksu gedit /etc/group


```

now just add your users to the firestarter group

---

### Post by thikrat on 2007-07-13
ahhh... so the sudoers file is not seeing system users, it only sees the users it has defined in the sudoers file itself?  That does make sense in a way, but shouldn't it also be able to understand the system groups?  

thanks

---

