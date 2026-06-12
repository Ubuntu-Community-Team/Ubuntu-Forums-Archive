---
title: "how to sort a word file by word size"
date: 2012-11-08
forum: General Help
---

### Post by Mia_tech on 2012-11-08
I have a text file with words, and I would like to sort it by word length/size. I checked the sort commands for any option that would allow me to do this, but none seem to work. 

thanks

---

### Post by Zill on 2012-11-08
Mia_tech:  Depending on how many words you have, you could paste them into a OpenOffice/LibreOffice spreadsheet in, say, column A.

Then enter a length formula (len) into column B and drag the formula down to the last row of data.

A quick sort based on column B will then sort the rows according to word length.

---

### Post by Mia_tech on 2012-11-08
> **Zill said:**
> Mia_tech:  Depending on how many words you have, you could paste them into a OpenOffice/LibreOffice spreadsheet in, say, column A.

Then enter a length formula (len) into column B and drag the formula down to the last row of data.

A quick sort based on column B will then sort the rows according to word length.

no I have to do it from a command line/script. I just was looking for a command, so I wouldn't have to write an algorithm to do it

thanks

---

### Post by Vaphell on 2012-11-08
```
while read w; do echo ${#w} $w; done < file | sort -n
```

---

### Post by Mia_tech on 2012-11-10
> **Vaphell said:**
> ```
while read w; do echo ${#w} $w; done < file | sort -n
```

how about if I only wanted to display the words and not the size?

---

### Post by SysBoot on 2012-11-10
take out the ${#w} part

---

### Post by Vaphell on 2012-11-10
no, that part makes sorting possible, you can only get rid of it after *sort*, let's say by adding *cut*
```

while read w; do echo ${#w} $w; done < file | sort -n **| cut -d' ' -f2-**
```

*-f2-* will make it print fields 2+. While you have single words here and *-f2* would do, it's just a special case of 'sort lines by their length' which the code does in reality. 2+ means proper printing if you wanted to use it to sort sentences by length or whatever :)

---

