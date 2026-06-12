---
title: "How to delete all instances of &quot;&lt;a href=(maybe a no/ letter/ sign)&lt;/a&gt;&quot; from a file."
date: 2013-05-29
forum: General Help
---

### Post by Peterinall on 2013-05-29
Hello folks,
     Again have hundreds of large file, from where i want to delete all internal and external link with their texts. Any idea about how can i do so with SED or ant other utility in commandline or script.

Basically i have to delete ```
<a href=(maybe a no/ letter/ sign)</a>
``` . The bracketed portion is highly changeable so looking for a sophisticated wildcard actually.

Thanks for your time.

---

### Post by HiImTye on 2013-05-29
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
sed -ie 's|<[a-zA-Z] href.*\/[a-zA-Z]>||' fileOrFiles
```

---

### Post by Peterinall on 2013-05-29
I think i have made a little mistake. Sorry. Actually the string patterns are ```
<a href="#[1-9]|[1-4][0-9]|50">See [1-9]|[1-4][0-9]|50</a>
``` and ```
<a href="#[1-9]|[1-4][0-9]|50">See [1-9]|[1-4][0-9]|50</a> and <a href="#[1-9]|[1-4][0-9]|50"> [1-9]|[1-4][0-9]|50</a>
```

sed have to delete both the 1st one and the 2nd one.

Thanks guys for your time n help.

---

### Post by HiImTye on 2013-05-29
> **HiImTye said:**
> ```
sed -ie 's|<[a-zA-Z] href.*\/[a-zA-Z]>||' fileOrFiles
```

will grab
```
<a href=blah blah junk></a>
<Z hrefblahblahblah/q>
```
etc
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Peterinall on 2013-05-30
I guess that "e" in the command is an trouble besides your code does remove some <a href= ...../> but deleting whole lines after the link anchor and it is also not working properly to remove all instances of <a href=**>.

---

### Post by HiImTye on 2013-05-30
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I didn't undrrstand what your last comment was. give some specific examples of what yoi need that isn't being done, or you need done diffrrently, and I can give you some examples of how to achieve them.

---

### Post by prodigy_ on 2013-05-30
To catch and strip only <a></a> tags i'd suggest:
```
sed -e 's|</\?a[^<>]*>||g' < infile > outfile
```
Should work in most situations.

---

### Post by Peterinall on 2013-05-30
Ya it is working nicely. Can you please describe the code a lil bit, so i can use them in informed way. 

Thanks for your time and help.

---

### Post by prodigy_ on 2013-05-30
Well, the **s** command tells sed we're doing pattern replacement (substitution). **|** characters separate the pattern to math, substitution string (which is empty in this case) and sed commands. Finally the **g** command tells sed to do more that one substitution per line if necessary.

**</\?a[^<>]*>** is the patthern we're looking for. Outer < and > are literals. /\? matches slash or nothing. a is literal. [^<>]* matches zero or more occurrences of anything that isn't < or > (regular expressions are greedy so without this part sed would remove a lot more than we wanted).

If you want to learn sed, start here (nice tutorial with lots of examples):
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

---

