---
title: "tar question"
date: 2007-04-14
forum: General Help
---

### Post by fernando_lopes_jr on 2007-04-14
I want to cpmpress same directorys using tar I've been using the comand:

> tar -cjf ABC.tar.bz2 /home/AAA/ /home/BBB/ /home/CCC/;

but the archive only compreses the content of the AAA directory how can I make it compress the BBB and CCC directory.

Thanks4help

---

### Post by energiya on 2007-04-14
Well, I use tar in a small backup script, and
```

tar cjf ABC.tar.bz2 /home/AAA /home/BBB /home/CCC

```
works very well.

---

