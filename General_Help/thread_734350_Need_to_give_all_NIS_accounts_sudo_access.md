---
title: "Need to give all NIS accounts sudo access"
date: 2008-03-24
forum: General Help
---

### Post by taliosfalcon on 2008-03-24
Every user here gets full administrative access to every desktop machine(very technically oriented company, and security isn't that big of a concern), we're switching over to Ubuntu and i'm trying to figure out how to give all NIS accounts sudo access automatically. Is there any way to do this? If not I suppose my only choice will be to enable the root account and distribute that.

---

### Post by bwhite82 on 2008-03-24
Use visudo. From a terminal:
> 
sudo visudo

Add whichever usernames you wish to that file. It uses Vim (which I personally hate) so its a little tricky to navigate. Can't remember how to set it to use nano. At any rate you could 'man vim' if you're having trouble using it.

---

### Post by taliosfalcon on 2008-03-24
> **Soldierboy said:**
> Use visudo. From a terminal:


Add whichever usernames you wish to that file. It uses Vim (which I personally hate) so its a little tricky to navigate. Can't remember how to set it to use nano. At any rate you could 'man vim' if you're having trouble using it.

The problem is we have about 60 employees that will need to have sudo access to every desktop and a desktop for each of those users, it makes it rather impractical to push out a new /etc/sudoers file every time a user is added/removed.

---

### Post by pointone on 2008-03-24
Make each of those users members of the "admin" group, or if they're all already in a group, add that group to your sudoers file.

---

