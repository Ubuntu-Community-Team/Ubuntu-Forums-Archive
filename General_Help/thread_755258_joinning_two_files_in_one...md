---
title: "joinning two files in one.."
date: 2008-04-14
forum: General Help
---

### Post by Mia_tech on 2008-04-14
how could I join the content of two text file into one?


thanks

---

### Post by bodhi.zazen on 2008-04-14
```
cat file1.txt file2.txt >> joined.txt
```

---

### Post by panayk on 2008-04-14
```
cat file1 file2 file3 > output
```

EDIT: Oops, too late! :)

---

### Post by lundholmj on 2008-04-14
cat $file >> $file

adds one file to the end of another

---

### Post by ghostdog74 on 2008-04-14
> **lundholmj said:**
> cat $file >> $file

adds one file to the end of another

no it does not. the variable is the same.

---

### Post by russo.mic on 2008-04-14
The Real answer to his question is cut and paste. -  sorry, tongue in cheek humor.

---

