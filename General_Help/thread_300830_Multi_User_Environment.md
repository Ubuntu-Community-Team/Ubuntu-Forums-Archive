---
title: "Multi User Environment"
date: 2006-11-16
forum: General Help
---

### Post by MikeAnix on 2006-11-16
I want to set up my Ubuntu PC so that every member of my family can have her/his own user id.  So far, this is easy.

What I can not figure out though, is how, as the "sys admin", I could install software that can be used by only one user, or how can any user can make changes to their environment without messing up with the other family member's environment.

Any suggestion will be appreciated.

Michel

---

### Post by Nameless_one on 2006-11-16
I think that if users have passwords, each will have to type in their password to access the files that belong to their profile. That keeps them seperated. 

I also think that you can put them all in a group, and whatever you want to be accessible to all of them, give it to the group (no matter the owner) and give them read/write permissions. 

Try running ```
gksudo nautilus
``` an look at the permissions tab in each file's and folder's properties.

---

### Post by MikeAnix on 2006-11-16
Will this approach allow, for example, each user to have their own Firefox bookmarks?

It would also be great if each user can choose which email client the use, and keep their message to themselves.  Same applies to Instant Messaging application!

---

### Post by Nameless_one on 2006-11-16
Firefox bookmarks are kept in your user folder, and each user has their own user folder (in /home/<username> - you have one, check out the hidden files), so yeah, each will have their seperate bookmarks. 

I'm not sure about the email client, but my guess is yes. I suppose each user can have his seperate anything, from profiles to whatnot, if you know how to do it.

---

### Post by CatKiller on 2006-11-16
Thunderbird certainly keeps seperate user profiles. The others will unless they are fundamentally broken, although I haven't technically used any others on Linux. By default, the only place your users will be able to write to is their Home folder, and that is where their configuration is stored. 

Installing software so that only one user can use it would be fiddly but doable, but I suspect that isn't what you meant. And if people wish to use different software from each other, it's easy enough to install all the different programs and they'd each choose the one they wanted to use.

As Nameless_one suggests, you should look in your own Home folder (Ctrl-H to view hidden files) to see the kind of configuration that gets stored there.

---

