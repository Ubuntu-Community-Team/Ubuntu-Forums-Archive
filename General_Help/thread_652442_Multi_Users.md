---
title: "Multi Users"
date: 2007-12-28
forum: General Help
---

### Post by techgeek40 on 2007-12-28
This is what I would like to do:

I have three users (richard, tech, testing)

I want all three to see the same documes/pictures/videos folder

So if I am in richard - edit a document and close that document out - go into tech and I want to edit that document - I can go into "documents" and open it up

Like in XP/VISTA - I can map all users to a "folder" where I have all documents and pictures in one location but all users see that one location (not shared folders)

Is there a way to do that in Ubuntu Gutsy?

---

### Post by taurus on 2007-12-28
Why not create a partition and mount it to /media/share through /etc/fstab.  Then, give permissions for everybody to write to it.  Now, you can edit whatever you want in there, whatever you happen to log in at that time.

---

### Post by Lostincyberspace on 2007-12-28
You cant really do that since you need the permissions of the home folder to be for one user in order to login.

---

