---
title: "wine multi-user installation issue"
date: 2008-03-20
forum: General Help
---

### Post by groovomata on 2008-03-20
Hello All, 
I had to do an installation of Microsoft Word 2003 using Wine to to be able to edit some Microsoft Word Documents natively (I know, booo, hisss!). Anyways, when logged in as myself I had no problem to run Microsoft Word. However when logged in as another user I can't find any menu options and when I checked out the .wine folder I found no sign of the Microsoft Word program I installed. Does anyone know how to add my installation for all the users of my computer?
Thanks,
Erik.

---

### Post by forrestcupp on 2008-03-20
Each user has a separate .wine folder with installed programs.  So if you installed Word as User1, User2 will have to go to /home/User1/.wine to find the Word that was installed.

One thing that you can do to help out is if you are going to install everything as User1, you can log in as User2 and run winecfg and set the drive mapping for C: to User1's .wine directory.

You may need to give permission in that directory to User2, though.

---

### Post by groovomata on 2008-03-27
Hmmm, thanks for that. I'll give a try and post back.
Thanks!

---

