---
title: "Data Modeling software"
date: 2007-03-26
forum: General Help
---

### Post by Invictus9 on 2007-03-26
Can anyone recommend a good database modeling software for linux/ ubuntu, preferably a free one? I need something that shows table structures, Primary/Foreign key relationships, and so on.

---

### Post by bytesmythe on 2007-03-29
The only one I've seen in the repos so far is "ferret". I haven't installed it yet, so I can't attest to its quality. One feature that the current release *doesn't* have is the ability to reverse-engineer existing databases.

[http://www.gnu.org/software/ferret/project/what.html](http://www.gnu.org/software/ferret/project/what.html)

Edited to add:
This one is open source and apparently does reverse-engineering. I'm going to download and try it:
[http://fabforce.net/dbdesigner4/index.php](http://fabforce.net/dbdesigner4/index.php)


More edits:
The dbdesigner4 software didn't seem to work.  If you're working with MySQL, try this:
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

I downloaded the x86/64 tar version, extracted it, and it actually ran without a hitch. Of course, I haven't tried to actually DO anything yet, so we'll see how it goes.

---

### Post by wolfear on 2007-06-10
Just an fyi-
There is a work around for DBDesigner4 :
[http://en.wikibooks.org/wiki/MySQL/Databases_manipulation]("http://en.wikibooks.org/wiki/MySQL/Databases_manipulation") 

I have no idea for sure if the above fix actaully works. Haven't tried it yet.

I'm not sure about Workbench (the visual designer from MySQL to replace DBDesigner), but as far as my personal experience goes, Workbench is unusable at present until a total re-write is completed in late 2007 (that estimate was from last time I checked, which has been several months)

---

### Post by fredy on 2008-03-19
workbench, is in beta and has a lot of bugs.
FWD engineer is a mess
try SQLPOWER open source POWER*Architect
(  FWD engineer works for mySQL, also)

---

