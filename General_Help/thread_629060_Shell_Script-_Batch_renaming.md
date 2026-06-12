---
title: "Shell Script- Batch renaming"
date: 2007-12-01
forum: General Help
---

### Post by geforceter on 2007-12-01
Hello people...
I need to do these in a shell script....
[LIST=1]
[*]Arrange all the files in the current directory in alphabetical order
[*]Prefix a number according to their alphabetical arrangement
[/LIST]
e.g. files:  z.txt, a.txt, f.txt
    become 01- a.txt, 02- f.txt, 03- z.txt

thank you

---

### Post by HermanAB on 2007-12-02
Here is what you need:
ls, sort, mv

---

### Post by yabbadabbadont on 2007-12-02
Sounds like someone wants us to do his homework for him...  :D

---

### Post by geforceter on 2007-12-02
Yup....
the homework was to move files in a folder to other folders based on their extentions and then number them according to their alphabetical order.....
i did the first part but am stuck at the second part

i know that i need to use **mv** to rename the files.....
but i do not know how to prefix the file name with the number after  sorting it

---

### Post by geforceter on 2007-12-02
any help...
i am stuck.....
i do not know how to arrange the files alphabetically and also how do i prefix them?

---

### Post by geforceter on 2007-12-02
ok i solved the problem....
here is the solution:
 ```

files=$(ls -1 | sort -d)
y=1
for x in $files
do
[INDENT]mv $x $y-$x[/INDENT]
[INDENT]y=`expr $y + 1`[/INDENT]
done

```

---

