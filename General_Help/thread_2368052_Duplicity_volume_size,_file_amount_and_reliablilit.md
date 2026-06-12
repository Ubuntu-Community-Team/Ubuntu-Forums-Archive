---
title: "Duplicity volume size, file amount and reliablility"
date: 2017-08-06
forum: General Help
---

### Post by Rooster2000 on 2017-08-06
I have around 3,6 GB data to back up with Duplicity. With the default 25 MB volume size a full backup creates around 144 backup files. If I run an incremental backup once a day, after a year - assuming each of my incremental backups fit in one 25 MB backup file - I have a total of 509 backup files.

Although I don't have to operate on them manually, this sounds a lot to me. I became curious on why the default volume size is set so low. Is there some performance loss or greater risk of getting corrupted files if filesize would be for example 300 MB? With this volume size my full backup would create only 12 files, although daily incrementals would nevertheless rise the amount to 377 after a year. I remember having read somewhere, considering ISO installation files, that it is important to verify them after download, as large files have a high risk for becoming corrupted. Is this the reason why Duplicity is set to make small backup files by default?

Is there a rule of thumb on what point one should rather make a new full backup instead of incremental one? I remember when using Deja-Dup (a graphical front-end for Duplicity) years ago, it wanted to create a full backup after 2-3 months of daily incremental ones. According to authors of Deja-Dup:
> Déjà Dup will occasionally make fresh full backups  for you.  This takes up more space and more time, but offers the  following benefits:

[LIST]
[*]Sometimes  there are bugs.  If a bug appeared in the middle of a chain of a year  of incremental backups, you would lose 6 months of backups.  Now, bugs  aren't expected, but better safe than sorry.  The occasional full backup  prevents hideously long chains of incremental backups, which can be  risky. 
[/LIST]
[INDENT] [...]
[/INDENT]
 
Déjà Dup assumes that [...] safety of data is paramount.
[SIZE=1] [SIZE=2][https://wiki.gnome.org/Apps/DejaDup/HowItWorks](https://wiki.gnome.org/Apps/DejaDup/HowItWorks)

That sounds reasonable to me, although would like to hear some exact definition for *hideously long chains of incremental backups*.
[/SIZE]
[/SIZE]

---

### Post by Rooster2000 on 2017-08-09
Bump.

---

### Post by Rooster2000 on 2017-09-10
I asked about this from the author of Duplicity, *Kenneth Loafman*. In his response, he concluded that in general, long backup chains are not suggested. There was no technical argument for this though, only practical one, being that if one of the incremental files gets damaged, one is unable to restore the incremental backups made after that point.

I found also [this]("http://lists.nongnu.org/archive/html/duplicity-talk/2007-07/msg00091.html") thread back from 2007 from the Duplicity mailing list, but it is only about volsize's effect on memory usage.

I conclude from this that increasing the default volume size doesn't have any significant or well-known effects on backup reliability.

---

