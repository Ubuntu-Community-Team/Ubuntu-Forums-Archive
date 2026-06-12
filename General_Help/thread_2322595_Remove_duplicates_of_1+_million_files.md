---
title: "Remove duplicates of 1+ million files"
date: 2016-04-29
forum: General Help
---

### Post by ndstate on 2016-04-29
Hello,

I have a 5tb hard drive that has over 1 million files (photos, music, documents, etc.) that are duplicates of other files and I need to delete the duplicates. I tried both fslint and dupeGuru but they both keep freezing and I cannot get the job done. Is there a program where I can merge folders together and have the program check the md5 or something to ensure I am overwriting the same files? (Basically this problem came about from creating backups and not deleting old backups. I think it would just be easiest to combine the folders and use md5 or something to ensure only the same files get over written). A gui is preferred.

Thank you

---

### Post by ndstate on 2016-05-01
Anyone have any ideas? Thank you.

---

### Post by dragonfly41 on 2016-05-01
I would try **FSlint** in Ubuntu Software Centre.

Also **Meld**.

[Later edit]

Reading again I see that you have already tried FSlint so perhaps try Meld.

And ..
> [COLOR=#000000]I have a 5tb hard drive [/COLOR][COLOR=#000000]
It may be that you are giving these utilities too big a bite of data to process and so you hit a freeze.

I would try breaking up the 5TB into (say) eight or more chunks.

group1
group2
...
group8

Apply FSlint (or Meld) to each group to eliminate duplicates.
Then merge group1 + group2 and reprocess with FSlint or Meld.

etc. until you have a manageable data set to do a final run.


[/COLOR]

---

### Post by pat4 on 2016-05-01
What about running fdupes from the CLI?

---

