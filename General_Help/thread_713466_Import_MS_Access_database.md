---
title: "Import MS Access database"
date: 2008-03-02
forum: General Help
---

### Post by muadnu on 2008-03-02
I'm pretty sure there'll be no way to achieve this, but I thought it was worth giving it a shot. I have an MS Access database that I made for my dad years ago, and I was wondering if there's any way to import it to any program that could work with Linux. I know it's possible to import the tables, but the database has lots of forms and macros and, unfortunately, some visual basic code. I don't have time to redo all that, but if I could import it somehow and get it to work after not that much work, I could wipe Windows off my dad's computer :). (Wine and Crossover don't run Access, at least not for Office 2003, though I've seen somewhere that Crossover might support it for Office 2000, which I haven't tested).

---

### Post by timjohn7 on 2008-03-06
I don't know whether you've received any reply to this, but I have exactly the same problem.  Based on the date of posting, I assume that the problem still exists!

---

### Post by muadnu on 2008-03-06
I haven't, but just in case, it seems like Access 2000 does work well with Crossover (maybe also Wine?), so that might be a solution (I haven't tried it myself). I actually wish I had never made the database in Access...

---

### Post by timjohn7 on 2008-03-06
I almost had success with Kexi.  Have you tried it?  All was looking well but Kexi crashed before it imported my database.  I'm also looking at rebuilding from scratch in Base, but time is precious!

---

### Post by muadnu on 2008-03-06
Kexi crashes for me too. I doubt it would import the Visual Basic code anyway...

---

### Post by orthodoc on 2008-03-24
I struggled with the mdb import issue for a long time. The solution is quite simple.

If you are using a terminal, this is what you need to do:
```
sudo apt-get remove kexi-mdb-plugin
```

followed by:
```
sudo apt-get install kexi-mdb-driver
```

Now the import process should work. The importing is however not perfect. Usually the date/time import is a bit tricky!! This way you will get all the tables, but no forms and reports.

---

### Post by muadnu on 2008-03-24
Thanks for the advice... I'll try it when I have time and let you know how it goes.

---

