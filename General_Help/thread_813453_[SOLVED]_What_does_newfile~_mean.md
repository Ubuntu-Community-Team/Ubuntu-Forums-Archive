---
title: "[SOLVED] What does newfile~ mean?"
date: 2008-05-30
forum: General Help
---

### Post by brett123 on 2008-05-30
When I use the Terminal to view my Desktop, I can see many old files that I have previously deleted, and emptied from the Garbage Bin.

All the files have ~ appended to them, eg:
newfile~
results.txt~
Unsaved Document~
...and so forth.

I can remove them with rm, but I am just wondering WHY they weren't removed when I deleted them via the GUI (right click 'Move to Garbage Bin')???

Any thoughts? Thanks.

---

### Post by RATM_Owns on 2008-05-30
If they have a ~ after them, then those are backup files automatically created.

---

### Post by brett123 on 2008-05-30
Like in automatic backups created every 10 minutes or something????

If so, how can I stop this from happening? I don't need auto backups, I save myself as required.

I'm just worried my disk will fill up with things I can't see (I rarely use Terminal to even know these exist).

Thanks again.


EDIT. Never mind, that was a stupid question I just asked. Of course I can find preferences in each program to stop the auto backups. :|

---

### Post by drs305 on 2008-05-30
> **brett123 said:**
> When I use the Terminal to view my Desktop, I can see many old files that I have previously deleted, and emptied from the Garbage Bin.

All the files have ~ appended to them, eg:
newfile~
results.txt~
Unsaved Document~
...and so forth.

I can remove them with rm, but I am just wondering WHY they weren't removed when I deleted them via the GUI (right click 'Move to Garbage Bin')???

Any thoughts? Thanks.

Some of the names you mentioned could be newer files than the ones you deleted. newfile~ and Unsaved Document~ are the types of filenames that are created when a process is interrupted or not fully completed, or autosaved. So it is possible you deleted it, only to have it created again at a later time.

As to your question, which editor are you using. For gedit, you can turn it off in Edit, Preferences, View, and then turn off the File Saving Options.

---

### Post by brett123 on 2008-05-30
Thanks. Yeah, gedit, and I did just find the option to turn it off.

I've only switched to Linux in the past week, so some times my mind is still spinning with the differences between Linux and Windows - I get confused easily (mainly the file system).

So, apologies in advance for any future silly questions I may ask. :D

---

### Post by drs305 on 2008-05-30
No problem -we've all been there. By the way, when a problem is solved the moderators would like us to mark the thread solved. You do that with the 'Thread Tools' link in the upper right corner near the first post. If you click on that link it opens and there is a Mark This Thread Solved link.

Welcome to ubuntu :)

---

