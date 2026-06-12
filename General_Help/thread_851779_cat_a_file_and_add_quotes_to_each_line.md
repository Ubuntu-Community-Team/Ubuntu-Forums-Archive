---
title: "cat a file and add quotes to each line?"
date: 2008-07-07
forum: General Help
---

### Post by svk on 2008-07-07
Suppose I have a list of filenames in a file called "include".  It looks something like this:
[FONT=Courier New]
[/FONT][INDENT][FONT=Courier New]serg@bijou:~$ cat include
file 1[/FONT]
[FONT=Courier New]file 2[/FONT]
[FONT=Courier New]file 3[/FONT]
[/INDENT]
I want to use whatever GNU terminal utilities or bash commands I have at my disposal to convert the output so that it looks like this:

[INDENT][FONT=Courier New]"file 1[/FONT]"
[FONT=Courier New]"file 2[/FONT]"
[FONT=Courier New]"file 3[/FONT]"

[/INDENT]Basically, I want to enclose each line in the file in double quotes.  Is there any way to do that?

---

### Post by sdennie on 2008-07-07
Try:

```

sed -e 's/.*/\"&\"/' some_file

```

---

### Post by moephan on 2008-07-07
> **vor said:**
> Try:

```

sed -e 's/.*/\"&\"/' some_file

```

If you want to save the output into a file, just redirect it into a new file

```

sed -e 's/.*/\"&\"/' include > include2

```

sed is probably the most powerful and flexible tool for this kind of thing ("sed" is short for "stream editor").

```

man sed

```

Python has easy to use tools for reading and writing files.
```

f= open("include","r")
f2 = open("include2","w")

lines = f.readlines()

for ln in lines:
 ln = ln.replace("\n","") 
 f2.write("\"" + ln + "\"\n")

```
[http://docs.python.org/tut/node9.html#SECTION009200000000000000000](http://docs.python.org/tut/node9.html#SECTION009200000000000000000)

Cheers, Rick

---

