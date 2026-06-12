---
title: "how can you concat all text files in directory to one file, that lists each filename?"
date: 2013-06-05
forum: General Help
---

### Post by fuzzylogic25 on 2013-06-05
Hi,

I have folders with all sorts of text files like html,php, etc. I need to print each one out and read the code. Now opening each one and printing them is a real pain. Because I like to copy it to a word doc and mess with the font/margins. How can I concatenate them all together under one file and be able to identify each file within it. 

For example say we have directory /home/test/ which contains following files:
-index.html
-process.php
-files.php
-output.html
-output.php

I could just go "cat * > alltext.txt" but then I wont know where within the file alltext.txt, process.php starts....so what I would like is something where alltext.txt would look like this:
================================
~~~~~index.html~~~~~~
....
...
..
....

~~~~~process.php~~~~~~
....
...
..
....

~~~~~files.php~~~~~~
....
...
..
....
==================================

I think you get my point. so this script would contact file1,file2,file3 together but also add a line saying "~~~~file2~~~~" for when file2 starts in the contcated file.

Thanks guys!

---

### Post by sudodus on 2013-06-05
Try ```
rm -i ../alltext.txt;for i in *;do echo "~~~ $i ~~~">>../alltext.txt;cat "$i">>../alltext.txt;done
```

---

### Post by Vaphell on 2013-06-05
capturing the output of the loop as a whole is much easier and cleaner
```
for i in *; do echo "~~~ $i ~~~"; cat "$i"; done > ../alltext.txt
```

---

