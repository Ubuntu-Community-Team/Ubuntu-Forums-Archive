---
title: "newbie q - how do I unrar multiple files"
date: 2005-06-11
forum: General Help
---

### Post by brickbat on 2005-06-11
Hi, I am trying to unrar multiple files like this but it gives me an error that the file is not found

unrar e -ad *.rar

It works on an individual file but it is not working with the *

ciao
bb

---

### Post by tread on 2005-06-11
find . -name *.rar -exec unrar e {}\;

either that or

find . -name *.rar -exec unrar e {} \;

---

### Post by brickbat on 2005-06-11
Hi, I tried both but I get

Usage: find [path...] [expression]

ciao
bb

Thanks for the quick reply.

---

### Post by brickbat on 2005-06-11
Its ok.  I got it. It was this command.

find . *.rar -exec unrar e -ad {} \;

Thanks

---

