---
title: "A program to search random data"
date: 2017-06-05
forum: General Help
---

### Post by FerryGnu on 2017-06-05
Hi,

In windows I had a program that had a series of database pages where all the data is indexed and can be retrieved with a random search. Pretty much like an FTS4 in SQLite database.

OK, that sounds confusing. Let's say the database has four records
rec 1: My mother went to the horse races yesterday and said it was great fun.
rec 2: Eggs with toast are my favourite.
rec 3: Pics from my weddings
rec 4: Racing cars is fun, but can get expensive.

If I search for "fun" it would return "rec 1" and "rec 4"

Not sure what one calls this kind of program, but is there something like this for Ubuntu, or do I have to write my own again?

Thanks, I hate reinventing the wheel.

---

### Post by dragonfly41 on 2017-06-05
**recoll** (in the repo) indexes all your files in your filesystem.
There is also python3-recoll which is a python wrapper for searching via recoll.

---

### Post by FerryGnu on 2017-06-05
Thanks, Sorry, I didn't make it fully clear. I don't need to search for any files, just the one database where I have entered the data into each record. Sorta like a diary where I can jump to pages that have the matching word.

Having said that, maybe "diary" is the program-type I am looking for. :)

---

### Post by dragonfly41 on 2017-06-05
**cherrytree** is a useful notes manager.

In cherrytree for "record" read "node".

I use cherrytree as my main notes keeper and I can
 quickly find nodes (records) where there is a search pattern match..

---

