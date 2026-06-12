---
title: "deleted files still taking up space"
date: 2007-01-17
forum: General Help
---

### Post by inhalentbroom on 2007-01-17
I seem to have a very strange problem.  I suppose I will start at the beginning.
I was doing a project for one of my classes where I had to research a backup utility and demonstrate it to the class.  During the demonstration, I guess I set up the software to run every night and to save my backups to my home directory.  Unfortunately, I was away from my computer for a while and by the time I had discovered this, my home directory's partition was almost half full from just backups.  Because the backups where owned by root, I opened a nautilus session as root and deleted the backups (I usually make backups to a 200 gig external harddrive).  Anyway, the files didn't go into the recycle bin, I assumed they had just been deleted.  Later, I noticed that they where still taking up harddrive space.  I have been unable to find the files (or anything) that could be taking up my harddrive space.  I even installed a program called graphical disk map, ran it on my home partition and it shows that only about 16 gigs are being used (Gnome system monitor says that 32 gigs are being used.)  Any ideas on how I can fix this?  I've tried everything I can think of and I've been unable to find any solutions using google.  Any help would be appreciated.  Thanks in advance.

---

### Post by Rippey on 2007-01-17
did you check /root/.Trash?

---

### Post by inhalentbroom on 2007-01-17
That managed to do it (well, /home/.Trash-root, close enough),  Well, now I feel stupid.  Thank you very much.  Fixed my problem completely.

---

### Post by Rippey on 2007-01-17
you're welcome :)

---

