---
title: "Permissions problem"
date: 2007-04-14
forum: General Help
---

### Post by cris on 2007-04-14
Right after loging into gnome , i get this message :
"User's $HOME/.dmrc file is being ignored. This
prevents the default session and language from being
saved. File shoud be owned by user and have 644
permissions. User's $HOME directory must be owned
by user and not writable by other users."

Is it bad ? What should I do to get things fixed ? 
I played yesterday with permissions , since i had some troubles with some files in my home directory. 
Thank you

---

### Post by energiya on 2007-04-14
If I undestand corectly, your problem is "$HOME/.dmrc". Just enter a terminal and type
```

chown USER:GROUP /home/USER/.dmrc

```
USER   = your user
GROUP = the users group

---

### Post by cris on 2007-04-14
Problem : I changed the permissions to my user's directory in /home , and gave acces permissions to a group. My initial group was the same as my username , but recently i changed group to root :D 
When i took a look at the directory's permissions , the group "user" had acces rights. Removed those , and at the Group section i choosed Root , and no permissions , and done. Rpoblem fixed.
Thank you

---

