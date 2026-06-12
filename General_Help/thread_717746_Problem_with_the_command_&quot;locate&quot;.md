---
title: "Problem with the command &quot;locate&quot;"
date: 2008-03-07
forum: General Help
---

### Post by nguyengiap on 2008-03-07
When I use the command "locate" to search a file (this file is exist) in a partitions fat32, there is no result found. This command work well with the other locations (\etc \var \usr ...).

---

### Post by Oldsoldier2003 on 2008-03-07
> **nguyengiap said:**
> When I use the command "locate" to search a file (this file is exist) in a partitions fat32, there is no result found. This command work well with the other locations (\etc \var \usr ...).

the database isn't set up to search your fat32 partition. look at man locate and you might be able to tweak locate's paths to include the fat32 partition but I'm not sure if its actually doable. I guess its something to play with or google :)

---

### Post by arvevans on 2008-03-07
Also, in a terminal window (CLI interface) do a "man updatedb" to see how to add other paths and filesystems to the 'locate' database.

Arv
_._

---

### Post by Oldsoldier2003 on 2008-03-07
> **arvevans said:**
> Also, in a terminal window (CLI interface) do a "man updatedb" to see how to add other paths and filesystems to the 'locate' database.

Arv
_._
and find / -name <filename> works too though  you may get a lot of garbage results over permissions if you don't run it under sudo

---

