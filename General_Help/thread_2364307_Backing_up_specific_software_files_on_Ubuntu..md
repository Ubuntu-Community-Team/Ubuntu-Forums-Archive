---
title: "Backing up specific software files on Ubuntu."
date: 2017-06-21
forum: General Help
---

### Post by mikeyk2 on 2017-06-21
I&#8217;m using Ubuntu and use something called Notes-Up; obviously a  notebook/office tool. When I go to my file browser and &#8220;view hidden  files&#8221;, I see Notes-Up and in that folder there&#8217;s one file. Notesup.db &#8212;  if I wanted to back up all of my notes, is that the file I&#8217;d need to  copy? Say I replace my hard drive but have that database file, if I install Notes-Up again and paste that old bd file in the root folder, will my notes be restored?

---

### Post by SeijiSensei on 2017-06-21
Here's a test you can try.  Look at the .db file and see what size it is and the date of last access.  Now add another note.  Does it get larger with an updated date?  Then it's pretty likely that's where your notes are stored.

---

### Post by mikeyk2 on 2017-06-21
> **SeijiSensei said:**
> Here's a test you can try.  Look at the .db file and see what size it is and the date of last access.  Now add another note.  Does it get larger with an updated date?  Then it's pretty likely that's where your notes are stored.

You nailed it, thank you! Yes, I did a test note and while the size didn't get bigger (it's measured in MB) the access time/last modified was the same as when I created the note/opened the software. I assume it means those are my notes.

---

### Post by SeijiSensei on 2017-06-21
OK, one last test just to confirm.  Close the application, navigate to the NotesUp directory, and rename the file to something like Notesup.db.old.  Now open the application.  You should have no notes and the application likely will have created an empty database.  If all that's true, then delete any new database and rename the old one back to Notesup.db.

Usually people back up their entire home directory which would back up this file as well.

---

