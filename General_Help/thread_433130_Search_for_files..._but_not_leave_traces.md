---
title: "Search for files... but not leave traces?"
date: 2007-05-04
forum: General Help
---

### Post by sudaca on 2007-05-04
Hello everybody this is my first post here. I need some help to erase traces (let say "names" that I had search for) in that part that says "the name contains:" If I do click in the down arrow (to the right of the text box) it show the names by which I have looked for before. Please, do you know how to erase or reset this field to show no names files or words.

---

### Post by ayoli on 2007-05-04
try in a terminal:
```
rm -f .recently-used*
```

---

### Post by sudaca on 2007-05-04
> **ayoli said:**
> try in a terminal:
```
rm -f .recently-used*
```

It doesn't work :(

---

### Post by ayoli on 2007-05-04
i forgot to mention to do that in your home dir:
```
rm -f ~/.recently-used*
```

---

### Post by sudaca on 2007-05-04
> **ayoli said:**
> i forgot to mention to do that in your home dir:
```
rm -f ~/.recently-used*
```

Still doesn't work.

---

### Post by ayoli on 2007-05-04
hmm, so i'm afraid that is due to gnome-searcn-tool which store somewhere your past entries, i have a look (in .gnome* dirs) but didn't find anything that match your query.

---

### Post by sudaca on 2007-05-04
Thanks for your help, but that's mean there is no solution?

---

