---
title: "chmod error turned files into directories? Eeeeeek!"
date: 2007-11-09
forum: General Help
---

### Post by klausbreuer on 2007-11-09
Hi everybody!

Yes, I was very tired. And screwed up.
But I don't know **how**.

I was in a terminal, trying to grant write access to some mp3 files, so I can update their tags.
And I messed up the chmod parameters order: I typed something like **chmod +r+w -R ***

And now all my mp3 files in the subdirectories here - have turned into subdirectories. Yes, subdirectories. And I don't know how to turn them back into files... :confused:

So I did chmod again, this time correctly. Which worked.
And if I - just for kicks - try to cd into a 'subdirectory', I get told that the command 'cd' wasn't found.

Hm. Could anybody please tell me how to turn these subdirectories back into files? Without destroying the subdirectory structure by affecting the . and .. ?

Many advTHANKSance!

Ciao,
Klaus

---

### Post by TheExplorer on 2007-11-09
1) How can you tell that the files have turned into subdirectories? What exactly has happened? Different color in mc/console or what?
2) What did you also do? Before chmodding?..
3) Try to fsck your hdd.

---

### Post by klausbreuer on 2007-11-09
> 1) How can you tell that the files have turned into subdirectories? What exactly has happened? Different color in mc/console or what?

An **ls -al **will show them to be directories and yes, their color has changed in Konsole 1.6.6.

> 2) What did you also do? Before chmodding?

Nothing else - file access worked well.

> 3) Try to fsck your hdd.

Will do, but would prefere to see if this can be fixed somehow - who knows what'll happen to the files if I run a fsck...

---

### Post by klausbreuer on 2007-11-09
Phew - a good friend of mine (you might know him from blog.fefe.de) fixed it for me:

find . -type d -exec chmod 755 \{\} \;

He said that the subdirectories were not executable anymore, and thus it could be opened and read - but no access to the contents...

I feel much relieved :)

---

