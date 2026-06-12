---
title: "Pipe into a for loop"
date: 2013-11-04
forum: General Help
---

### Post by hojjat on 2013-11-04
I want to send the output of some command into a for loop in bash. How can I do that?

Here is an example: let's say I want to run cat, and then send the output of it to a for loop, which reads each line, and tells you the character length of that line. It should be sometihng like:

cat FILE | for i in $1; do print length($i); done

But that doesn't really work. So how can I do that? (I don't want to write and save a script file, I want to do it all on the fly using pipes only).

---

### Post by steeldriver on 2013-11-04
You can do that kind of thing with **read** and **while** e.g.

```

while read line; do *something with* "$line"; done < file

```

No cats harmed in the making of this script (uses a < **input redirection** instead of piping from cat)

---

### Post by Impavidus on 2013-11-04
To show you a command I used to generate a list of words in a collection of tex files, sorted by word length:
```
[COLOR=#ff0000]cat file1.tex file2.tex file3.tex | \[/COLOR]
sed -f filterglscommands.sed | sed -f filterother.sed | \
tr -s ' ' '\n' | tr '[:upper:]' '[:lower:]' | sort | uniq | \
[COLOR=#ff0000]while read w; do echo ${#w} $w; done | \[/COLOR]
sort -n >wordlength.txt
```
Similar to what you're doing, you can take the red lines. **${#w}** returns the length of string **w**. The sed scripts are used to do some limited macro expansion and remove all other commands and interpunction.

---

### Post by sisco311 on 2013-11-04
hojjat, please check out  BashFAQ 001 (link in my signature). ;)

---

### Post by hojjat on 2013-11-06
All were very good answers. This one was my favorite :)

---

