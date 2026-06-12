---
title: "How to setup default home directory?"
date: 2008-04-04
forum: General Help
---

### Post by cpthk on 2008-04-04
Where do I setup default home directory? So when new users are created, his home directory where have default files instead of blank folder.

---

### Post by AndyCooll on 2008-04-04
Usually when you create a new user via System > Administration > Users And Groups a home directory is automatically created for them. And the first time they log in this directory will be populated by certain files. Is this not happening?

:cool:

---

### Post by cdenley on 2008-04-04
I think when you create new users with new home folders, their home folder is populated with the files in /etc/skel. I don't think you can change the path defaulting to /home/<user>, but you can specify a different path when adding the user, or change the home folder for an existing user.

---

### Post by mcduck on 2008-04-04
> **cdenley said:**
> I think when you create new users with new home folders, their home folder is populated with the files in /etc/skel. I don't think you can change the path defaulting to /home/<user>, but you can specify a different path when adding the user, or change the home folder for an existing user.

That's correct. Everything you put in /etc/skel is copied to new user's home directories.

---

### Post by cpthk on 2008-04-04
Yes, I think that's what I need. Because I am trying to put some documents, so everyone can see that in their home directory.

---

### Post by Tomatz on 2008-04-04
k

---

