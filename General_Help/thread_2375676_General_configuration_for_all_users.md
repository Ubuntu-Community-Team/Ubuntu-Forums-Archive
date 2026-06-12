---
title: "General configuration for all users"
date: 2017-10-26
forum: General Help
---

### Post by mrhollywood360 on 2017-10-26
I made a configuration that includes GNOME layout and some settings in a /temp directory. I want to copy this directory whenever a user logs in for the first time. My current way of trying this is a script in /etc/profile.d/ 
```
if [ ! -f $HOME/.nodelete ]
then
rsync -va /temp/ $HOME/        
touch $HOME/.nodelete        
chown -R $USER $HOME/
fi
```
But this gives me permissions errors. Is there a better way of doing this?

---

### Post by aromo2 on 2017-10-26
Why don't you simply copy the contents of /temp in /etc/skeleton/ ? That would achieve your goal (for new users).

---

### Post by efflandt on 2017-10-27
If you add a user with "sudo adduser" (or with gui System Settings > User Accounts) the contents of /etc/skeleton/ is put in their $HOME directory. Note that "sudo useradd" might NOT put anything in their $HOME or might not even create their $HOME, so use adduser instead if doing that from a terminal.

---

