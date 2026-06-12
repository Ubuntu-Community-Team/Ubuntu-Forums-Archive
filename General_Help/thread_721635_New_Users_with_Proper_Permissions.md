---
title: "New Users with Proper Permissions?"
date: 2008-03-11
forum: General Help
---

### Post by js1 on 2008-03-11
I'm using Kubuntu 7.10 amd64.  The initial user that gets created during install gets added to a bunch of groups listed in /etc/groups and /etc/gshadow:

> 
adm
dialout
cdrom
floppy
audio
dip
video
plugdev
scanner
lpadmin
admin


However, new users that get added to the system using adduser doesn't get added to those groups.  For kubuntu, if the user is not in the proper group, some things won't work, namely KMix. 

What's the proper way to add new users so that they are also added into the relevant groups?  Thanks for any clarification.

---

### Post by bodhi.zazen on 2008-03-11
You can do it from the command line with adduser :

use the -G flag :

[http://linux.die.net/man/8/adduser](http://linux.die.net/man/8/adduser)

I do not think you can do it from a GUI (graphical) tool.

---

### Post by sisco311 on 2008-03-11
you can use the usermod command to add an existing user to groups:
```
sudo usermod -a -G adm,dialout,cdrom,floppy,audio,dip,video,... username
```

---

### Post by js1 on 2008-03-11
> **sisco311 said:**
> you can use the usermod command to add an existing user to groups:
```
sudo usermod -a -G adm,dialout,cdrom,floppy,audio,dip,video,... username
```

Sorry for not being more clear in my original post.  The question is also, how am I suppose to know that those are the relevant groups to add a user into without looking in the /etc/group file first?

---

### Post by bodhi.zazen on 2008-03-11
Most groups are self explanatory.

I suggest you use audio, video, cdrom as a starting list.

If a user has problems, add one group at a time.

---

### Post by sisco311 on 2008-03-12
```
id -Gn *user_name*
```will print the groups of user_name.

You can use this command with the user  created during installation to get the list of  'relevant' groups.

NOTE: Placing the user in the **admin** group will give them administrator access rights(people who can *sudo*).

---

