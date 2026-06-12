---
title: "Sharing rhythbox database between users"
date: 2006-10-06
forum: General Help
---

### Post by honda on 2006-10-06
Hello,
I'd like several users to share the same rhythmbox database (otherwise I'll have to maintain all myself). I thought that would be easy with symbolic links, so I moved the rhythdb.xml file to a shared folder and made a symbolic link there (with nautilus), copied the link to the original place and it worked fine I thought. Until I realized that whenever I edited the database, rhythmbox would delete the link and rewrite the database file in my home folder. I thought this was nautilus fault so I googled up the 'ln' command and tried this instead: 
ln /home/Gemensam/musik/rhythmdb.xml rhythmdb.xml
, being where the original db file was. This too worked fine until rhythmbox again deleted the (this time 'hard', I think) link and rewrote the db file...

So have I misunderstood something about symbolic links? Or is it just rhythmbox that does this on purpose?

---

### Post by honda on 2006-10-09
Noone have any advice? What I'm trying to do is make rhythmbox use a database file on another location than usual by placing a symbolic link in the original place pointing to the other place. To me it appears as rhytmbox is replacing the link with a regular file when I edit the database. This seemingly makes symbolic links practically useless, so I guess I have misunderstood something. Could anyone care to enlighten me?

---

