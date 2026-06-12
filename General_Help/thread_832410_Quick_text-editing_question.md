---
title: "Quick text-editing question"
date: 2008-06-17
forum: General Help
---

### Post by cvp on 2008-06-17
I have a 15 GB XML file, and I want to find the line number of a specific line. I'm afraid to try to load it into any graphical text editor because it won't be able to load the entire thing into RAM.
Is there a text editor or text viewer that will NOT attempt to load the entire file, but will still be able to give me a line number for the line, and let me see what's around it?

Thanks in advance!
-cvp

---

### Post by sdennie on 2008-06-17
Rather than using a text editor, if you just want to know the line number of a line and you know exactly what the line looks like, you could use grep instead:

```

grep -n "exactly what the line looks like" huge_file.xml

```

That will print the line and the line number.

---

### Post by cvp on 2008-06-17
Awesome, I have the line number now. Thanks!
But is there another tool I can use to view the first dozen or so lines before that line and those after that *doesn't* attempt to load the entire file into RAM first?

---

### Post by sdennie on 2008-06-17
Grep to the rescue again!

To print the 1 line before the match:

```

grep -B1 -n "exactly what the line looks like" huge_file.xml

```

To print 5 lines after the match:
```

grep -A5 -n "exactly what the line looks like" huge_file.xml

```

To print 10 lines before and after the match:
```

grep -C10 -n "exactly what the line looks like" huge_file.xml

```

Hope that helps.  If not, I'm not sure what editor to use but, hopefully someone else will.

---

### Post by cvp on 2008-06-17
Sweet.
Thank you so much!

---

### Post by cvp on 2008-06-17
Just for the record, the line I was looking for was line #256,453,718 out of 259,427,121 lines total. :p

---

### Post by bodhi.zazen on 2008-06-17
If you have a line number you can also

grep -n # huge_file.xml

where # is the line number

---

### Post by sdennie on 2008-06-17
Wow, it probably would have taken a while to find that by hand...  ;)

If you are regularly working with xml files that large, you would probably find tools like grep, sed and perl very useful.  There is a huge amount of information on the internet about these tools so, you should be able find good tutorials.

---

### Post by cvp on 2008-06-17
[quote=vor]If you are regularly working with xml files that large, you would probably find tools like grep, sed and perl very useful. There is a huge amount of information on the internet about these tools so, you should be able find good tutorials.[/quote]
Oh, definitely. I'm a research intern, and most of my job is teaching myself Perl as I go. :p I could've written a simple Perl script to do all of this, but I figured there was some easier way with shell commands, and lo and behold, there were and probably are several other ways to go about it.
I love being paid to learn.

Anyway, thanks again!

---

