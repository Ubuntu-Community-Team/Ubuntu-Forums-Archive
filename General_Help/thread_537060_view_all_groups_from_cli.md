---
title: "view all groups from cli"
date: 2007-08-28
forum: General Help
---

### Post by reckless2k2 on 2007-08-28
how would i go about showing all available groups on my system from the command line? i'm not talking about the groups any user is a part of using "id" or "groups". i'm talking about showing all available groups on a system so i can pick current groups to add a user to or see the new groups i've added to add a user to. 

i'll looking to view all available groups on a system from the command line. 

thanks.

---

### Post by Seisen on 2007-08-28
Well depending on which type of text editor you like put this in the terminal

```
vim /etc/group
``` I use Vim so that is why I put it their but you can replace it to your liking.

---

### Post by reckless2k2 on 2007-08-28
hahaha...yeah i'm a goofball. the simple answer right in my face. i was looking for some crazy grep option or something. hahaha.

---

