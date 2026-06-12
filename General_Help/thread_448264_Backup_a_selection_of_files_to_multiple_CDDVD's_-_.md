---
title: "Backup a selection of files to multiple CD/DVD's - Compressed"
date: 2007-05-18
forum: General Help
---

### Post by musther on 2007-05-18
I'm looking for a nice straight forward way to back up a selection of directories to DVD's and/or CD's.  Basically what would be ideal would be to select a bunch of folders, have them compressed as much as possible, and then archived across a a load of CD's.  Of course some way to later gain access to the files is essential.

I thought maybe if there isn't a nice app to do this, there might be a command line tool, such as tar, which would add all the files to archives, stopping when they reach a certain size and starting a new one, something like:
```
tar --compress --some-other-options --maxsize=5600M -r *
```

Then I could symlink all the folders I want to backup to one place and run it, burning the output files to DVDs.

As you can see, I've not really used tar before.

---

### Post by adzik on 2007-05-20
I am currently looking to do something similar myself.
Although a couple solutions I have come across aren't perfect, they seem to be alright.
One utility you can have a look at is Mondo rescue:  [http://www.mondorescue.org/](http://www.mondorescue.org/)
The other option I have used in a couple instances is 7zip through wine.
I haven't had any problems using 7zip ever. It has a spanning option, so that helps with grabbing a selection of files and compressing, then burning it yourself.
Anyway, that's a start I suppose. I'm sure there is more out there then just this.  :D

---

### Post by dgrafix on 2007-06-21
This is exactly what i want to do!!
Please dont tell me pkzip on dos has something even the mighty TAR cannot do! (as far as i can tell :/)

Did any of you find a way in the end?

---

