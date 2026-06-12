---
title: "Search help"
date: 2008-05-09
forum: General Help
---

### Post by tattrat on 2008-05-09
In ubuntu, how do I search for a text string occurring inside a file, rather than inside a filename, and easy one to crack I am sure, I just don't know how!!

---

### Post by Monicker on 2008-05-09
well, from a terminal you can do
```

grep string file.txt
```

Is this a regular text file?  That is the default for grep, so you would need different options for a binary file.

Also, searches are case sensitive, unless you do 
```

grep -i string file.txt
```

---

### Post by tattrat on 2008-05-09
I do not know the file name; I want to find the name of the file in which the string of text occurs. The files are source code.

---

### Post by tattrat on 2008-05-09
anybody?

---

