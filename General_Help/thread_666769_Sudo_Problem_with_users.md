---
title: "Sudo Problem with users"
date: 2008-01-13
forum: General Help
---

### Post by MK_MIke on 2008-01-13
Hello,

I had a problem with forgetting my username and pasword for a system i'm working i went into resuce mode on the cd and change the root password. and booted up and remade the users via console

Problem: i can no longer use sudo for my main acount i cant figure out how to make it work again. it has somthing to do with me no t being in right group i cant see the groups becuse i dont know what the command to view them is....

Can anyone help me put my user back in to the groups it should be so i can use sudo again?

Sorry if this has been posted before.

---

### Post by machoo02 on 2008-01-13
You need to add your main user account to the admin group.  Start up in single user mode, and enter```
adduser name admin
```substituting the username you would like to add to the admin group with name

---

### Post by MK_MIke on 2008-01-13
Thinks for the reply,

i did the command "adduser mknights admin" which didnt work it failed with with this message
> adduser: The group 'admin' does not exist

Any idea's what i can do from here?

---

### Post by capink on 2008-01-13
```
sudo groupadd -g 114 admin
sudo usermod -a -G admin [COLOR="Red"]username[/COLOR]
```

Replace [COLOR="#ff0000"]username[/COLOR] with your user name.

---

### Post by bwhite82 on 2008-01-13
Boot to safe mode.

> nano /etc/sudoers

Add the following line:

> yourusername	ALL=(ALL) ALL

Save. Then:

> login

And:

> startx

---

### Post by MK_MIke on 2008-01-13
Thanks that fixed it, but i didnt need to use the cd did it as root :P

---

