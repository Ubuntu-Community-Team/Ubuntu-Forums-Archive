---
title: "Sharing .xls files"
date: 2007-05-21
forum: General Help
---

### Post by drmbogo on 2007-05-21
Hi all!
I've gone ahead and set up my office network w/ Ubuntu, and so far I'm loving it. It seems every time I run into a problem, there's a solution just a few clicks away.
So, here's today's issue:
I need to share a spreadsheet between 3 computers, two of which are running Feisty, the third running XP. I've already set up NFS and Samba, and sharing the file works just fine, AS LONG AS the file is not open on any of the computers. I need to be able to update the spreadsheet while it's open on another computer, in much the same way that MS Excel can share a file, and update it 'live'. I use the sheet as a weekly production list, which my employees can update with the time they've spent on a project.
Anyone have any ideas? I've looked thru the help files in both OOo and Gnumeric, but neither mention filesharing...
As an alternative, is there a program that I could use for production/time management? (I hadn't considered this option 'til just now, so I'll do a little research in that direction)

Thanks in advance!

---

### Post by boredandblogging.com on 2007-05-22
This doesn't seem to be an option yet:

[http://qa.openoffice.org/issues/show_bug.cgi?id=8811](http://qa.openoffice.org/issues/show_bug.cgi?id=8811)
_[http://www.oooforum.org/forum/viewtopic.phtml?p=211852#211852](http://www.oooforum.org/forum/viewtopic.phtml?p=211852#211852)_

---

### Post by drmbogo on 2007-05-22
Thanks for the reply and the links! Seems they've been working on this issue for some time. Wish I had some programing experience to help!
Cheers

---

### Post by AlanRogers on 2007-05-22
drmbogo, in the interim, perhaps you could/should upscale your process?

A simple database, just one table, would a better application for this and there is a compatible MDB Viewer in Ubuntu that would enable you to use MS Access. This would give you record locking and stability, which sharing an Excel spreadsheet does not.

I haven't yet tried it but you should be able to make the database in Open Office and save it in an MS Access compatible format, if the MDB Viewer doesn't work. I'll try it out tonight though and post back. If you're willing to send me the file, I'll even test it on real data, rather than imaginary.

---

### Post by drmbogo on 2007-05-22
Hi Alan,
Thanks so much for taking the time to look into this. I tried sending you a PM with my production sheet attached, but the size is a hair too big (21kB, the limit is 19.5kB, arrgh!) Nothing too complex, I think your idea might work quite well. I have OOo installed on all my linux machines, so that might be the best way to go. I'm not familiar with MDB viewer, but I'm not opposed to learning :)
If i get a chance later tonight, I'll tar the .xls or .ods file and try to send it that way...
Thanks again,
dB

---

### Post by drmbogo on 2007-05-23
Hi Alan,
Sorry, didn't get a chance to do this last night. I also am not able to send an attachment in a PM, so here's the file...
Thanks again for your help
Dave

---

