---
title: "Login"
date: 2007-10-10
forum: General Help
---

### Post by AgentZ86 on 2007-10-10
Hi all,

Regarding login,

When I installed Ubuntu I basically created a user thinking I would get to a screen for root creation but that never happened.

So basically I login with the user that was created on initial install and this appears to be the root as well ???

But when I install programs etc. then I'm asked for the pass which is the same as my user pass.

Is this right ? 

I'm thinking I should have created the user and login and use my machine as a standard user, not as root ???

What will this do to my package installs will I have to login as root to install them or will this happen automatically ???

Please advise I'm a little confused about this subject.

Thanks

---

### Post by aJayRoo on 2007-10-10
Read [this](https://help.ubuntu.com/community/RootSudo) documentation page, it should explain everything. If not then feel free to post back with any outstanding queries.

---

### Post by AgentZ86 on 2007-10-10
> **aJayRoo said:**
> Read [this](https://help.ubuntu.com/community/RootSudo) documentation page, it should explain everything. If not then feel free to post back with any outstanding queries.

Thanks for the reply,

So let me make sure I understand ?

So all are acting as root, but really no root access unless prompted or logged into a terminal as root ??

But what about other users does that work the same for them when I add addtional users to this computer ? and the root password will now be whatever that users password now is ?

I'll re-read this but thats what it sounds like to me.

So I'm understanding that use of the default user I created when first installing the system is now ok, and no need for creating additional users, just to avoid being logged in as root ? As most other distros typically require  for security reasons ???


Please advise
Thanks

---

### Post by rsambuca on 2007-10-10
I believe when adding new users, they do not have sudo privileges unless you specifically add them to the sudoers file.

---

### Post by Ptero-4 on 2007-10-10
Only users that belong to the "admin" group have sudo privileges.

---

### Post by zvacet on 2007-10-10
In **users&groups** create new user and in properties give him all privileges exept admin.Most of the time you will work as that kind of user because it is safe (from you and from others).Only when you need to install or do anything else involving sudo you will use your firs account.

---

### Post by AgentZ86 on 2007-10-10
> **zvacet said:**
> In **users&groups** create new user and in properties give him all privileges exept admin.Most of the time you will work as that kind of user because it is safe (from you and from others).Only when you need to install or do anything else involving sudo you will use your firs account.

Thanks all, 

So if I go to Users and Groups, I have 2 users, root, and user1

user1 has almost all privileges and is part of a group called user1

The root has no privileges and is part of a group called root

I'm not sure why, basically that is what I have from a default installation.

So what is the default user during installation, is that a root / admin user ?

So, then I would have to add another user, and login as that user

Or could I just change the current user to have no admin privileges ??

But if that is the root user, then will I have root priviledges ??

I don't really understand it, 

I just want to login as a user, and have the root separate as I have done with all the other distro's 

????:confused:

---

