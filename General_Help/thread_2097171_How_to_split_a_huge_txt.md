---
title: "How to split a huge txt"
date: 2012-12-22
forum: General Help
---

### Post by baffodoro on 2012-12-22
Hello All, 
I have a huge txt file (1,5 gb) and i need to split in smaller txt files (max 150 mb) in order to upload it in a calc sheet.
Does anybody know if there is a software to do so without using the command line (with which i do not have such confidence?)

Thank you ):P

---

### Post by vanadium on 2012-12-22
If not using the command line, I would think of using a good text editor.

---

### Post by sisco311 on 2012-12-22
gnome-split is in the repositories (universe). Or you can try [HJSplit]("http://www.hjsplit.org/linux/").

---

### Post by vanadium on 2012-12-22
Take care, when using these tools, whether they allow you to split per number of lines. You do not want to split your text file in a binary way, where lines would be cut in half. The command line utility "split" by default splits text files per 1000 lines.
```

split yourinputfile.txt

```
would be all you need to have your text file split into files, each of 1000 lines long.

---

### Post by sudodus on 2012-12-22
> **vanadium said:**
> Take care, when using these tools, whether they allow you to split per number of lines. You do not want to split your text file in a binary way, where lines would be cut in half. The command line utility "split" by default splits text files per 1000 lines.
```

split yourinputfile.txt

```
would be all you need to have your text file split into files, each of 1000 lines long.
+1
split is a good tool. Read the manual for more details```

man split
```

---

### Post by baffodoro on 2012-12-26
Thank you all, I tried to use gnome splitter, which is quick but doesn't keep the lines together, so i tried to split with 'man split' and after reading the manual everything was easy and quick.
No problem and lines kept together.:D:D:D:D:D

---

### Post by sudodus on 2012-12-26
I'm glad it worked for you :KS

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

