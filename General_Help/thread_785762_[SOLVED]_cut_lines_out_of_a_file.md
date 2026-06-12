---
title: "[SOLVED] cut lines out of a file"
date: 2008-05-07
forum: General Help
---

### Post by borobudur on 2008-05-07
Hi,
I would like to cut some lines out of a file after a certain pattern. I was thinking of ***awk*** or ***grep*** but I don't find it (but I can't look for the whole line just a part of it). 

Thanks

---

### Post by Monicker on 2008-05-07
Can you be a tad more specific?  Are you wanting to retrieve certain lines from a file, or remove them?  What do you mean about you can only look at part of a line?

An example of what you are trying to do would be very helpful.

---

### Post by davidpbrown on 2008-05-07
Maybe try sed?

There's a very good introduction to sed at [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

### Post by bodhi.zazen on 2008-05-07
This is a nice reference.

[http://www.linuxtopia.org/online_books/gnu_linux_tools_guide/text-manipulation-tools.html](http://www.linuxtopia.org/online_books/gnu_linux_tools_guide/text-manipulation-tools.html)

Depending on how complex this is, you can use grep and cut.

grep -n pattern file #to list line numbers.

cut 1,3,5-7 file > new_file

---

### Post by borobudur on 2008-05-07
Sorry my english could be better...

Example:
remove all lines which includes ***xyz***:

1 - bla bli blu
2 - bla bla bal **xyz** bla
3 - bli blu blum

I want to get rid of line 2.

---

### Post by Monicker on 2008-05-07
You could also use grep for your example:
```

grep -v xyz file.txt > newfile.txt
```

---

### Post by bodhi.zazen on 2008-05-07
If you know the line number, you use sed like this :

sed -e '3d' file > file_cut

---

### Post by borobudur on 2008-05-07
[Monicker]("http://ubuntuforums.org/member.php?u=558830") thanks!

---

